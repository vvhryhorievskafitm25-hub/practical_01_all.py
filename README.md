# practical_01_all.py
"""
Практична робота №1: Розробка програмних модулів з використанням 
базових операторів, умовних конструкцій та циклів.
Виконано студенткою групи КБ-25: Григор'євська
"""

import math


# ==========================================
# ЧАСТИНА 1. Завдання 1.1: Математичні вирази
# ==========================================
def task_1_1():
    print("\n--- Завдання 1.1: Обчислення математичних виразів ---")
    try:
        a = float(input("Введіть a: "))
        b = float(input("Введіть b: "))
        c = float(input("Введіть c: "))
    except ValueError:
        print("Помилка: введіть числові значення.")
        return

    sum_squares = a**2 + b**2 + c**2
    average = (a + b + c) / 3
    discriminant = b**2 - 4 * a * c
    hypotenuse = math.sqrt(max(0.0, a**2 + b**2))
    is_triangle = (a + b > c) and (a + c > b) and (b + c > a)

    print(f"  Сума квадратів: {sum_squares:.2f}")
    print(f"  Середнє арифметичне: {average:.2f}")
    print(f"  Дискримінант: {discriminant:.2f}")
    print(f"  Гіпотенуза (за катетами a, b): {hypotenuse:.2f}")
    print(f"  Чи утворюють сторони трикутник: {is_triangle}")


# ==========================================
# ЧАСТИНА 1. Завдання 1.2: Конвертор типів
# ==========================================
def task_1_2():
    print("\n--- Завдання 1.2: Стандартні функції та типи ---")
    raw_input_val = input("Введіть значення: ")

    try:
        val_int = int(raw_input_val)
    except ValueError:
        val_int = "Неможливо конвертувати у int"

    try:
        val_float = float(raw_input_val)
    except ValueError:
        val_float = "Неможливо конвертувати у float"

    val_bool = bool(raw_input_val)

    print(f"  Значення як int: {val_int} | Тип: {type(val_int)}")
    print(f"  Значення як float: {val_float} | Тип: {type(val_float)}")
    print(f"  Значення як bool: {val_bool} | Тип: {type(val_bool)}")
    print(f"  Чи є введене значення строкою: {isinstance(raw_input_val, str)}")

    name = input("Введіть ім'я: ")
    age_str = input("Введіть вік: ")
    try:
        age = int(age_str)
        print(f"  Користувач: {name:<10} | Вік: {age:03d} років")
    except ValueError:
        print(f"  Користувач: {name:<10} | Вік введено некоректно: {age_str}")

    sample_range = list(range(1, 6))
    print(f"  Згенерований список range(): {sample_range}")
    print(f"  Довжина списку (len): {len(sample_range)}")
    print(f"  ID об'єкта в пам'яті (id): {id(sample_range)}")


# ==========================================
# ЧАСТИНА 2. Завдання 2.1: Шкала ЄКТС
# ==========================================
def classify_grade(score: int) -> str:
    if 90 <= score <= 100:
        return "A"
    elif 82 <= score <= 89:
        return "B"
    elif 74 <= score <= 81:
        return "C"
    elif 64 <= score <= 73:
        return "D"
    elif 60 <= score <= 63:
        return "E"
    elif 35 <= score <= 59:
        return "FX"
    else:
        return "F"


def task_2_1():
    print("\n--- Завдання 2.1: Класифікація оцінок за ЄКТС ---")
    try:
        score = int(input("Введіть оцінку (0-100): "))
        if score < 0 or score > 100:
            print("  Помилка: оцінка має бути від 0 до 100")
        else:
            grade = classify_grade(score)
            print(f"  Оцінка {score} → ЄКТС: {grade}")
            passed = grade not in ("FX", "F")
            print(f"  Результат: {'Зараховано' if passed else 'Не зараховано'}")
    except ValueError:
        print("  Помилка: введіть ціле число.")


# ==========================================
# ЧАСТИНА 2. Завдання 2.2: Тип трикутника
# ==========================================
def triangle_type(a: float, b: float, c: float) -> str:
    if not (a + b > c and a + c > b and b + c > a):
        return "не є трикутником"
    sides = sorted([a, b, c])
    is_right = abs(sides[0]**2 + sides[1]**2 - sides[2]**2) < 1e-9

    if a == b == c:
        return "рівносторонній"
    elif is_right:
        return "прямокутний"
    elif a == b or b == c or a == c:
        return "рівнобедрений"
    else:
        return "різносторонній"


def triangle_area(a: float, b: float, c: float) -> float:
    p = (a + b + c) / 2
    return math.sqrt(p * (p - a) * (p - b) * (p - c))


def task_2_2():
    print("\n--- Завдання 2.2: Визначення типу трикутника та площі ---")
    try:
        a = float(input("Введіть сторону a: "))
        b = float(input("Введіть сторону b: "))
        c = float(input("Введіть сторону c: "))

        t_type = triangle_type(a, b, c)
        print(f"  Тип трикутника: {t_type}")

        if t_type != "не є трикутником":
            area = triangle_area(a, b, c)
            print(f"  Площа трикутника: {area:.2f}")
    except ValueError:
        print("  Помилка: введіть числові значення для сторін.")


# ==========================================
# ЧАСТИНА 3. Завдання 3.1: Цикл for
# ==========================================
def factorial(n: int) -> int:
    res = 1
    for i in range(1, n + 1):
        res *= i
    return res


def harmonic_sum(n: int) -> float:
    total = 0.0
    for i in range(1, n + 1):
        total += 1 / i
    return total


def multiplication_table(n: int) -> None:
    for i in range(1, n + 1):
        print("  ", end="")
        for j in range(1, n + 1):
            print(f"{i * j:4d}", end="")
        print()


def task_3_1():
    print("\n--- Завдання 3.1: Цикл for (факторіал, ряд, таблиця множення) ---")
    try:
        n = int(input("Введіть число n: "))
        if n < 0:
            print("  Число має бути невід'ємним.")
            return
        print(f"  {n}! = {factorial(n)}")
        print(f"  Гармонічна сума H({n}) = {harmonic_sum(n):.6f}")
        print(f"\n  Таблиця множення {n}×{n}:")
        multiplication_table(n)
    except ValueError:
        print("  Помилка: введіть ціле число.")


# ==========================================
# ЧАСТИНА 3. Завдання 3.2: Калькулятор (while)
# ==========================================
def task_3_2():
    print("\n--- Завдання 3.2: Інтерактивний калькулятор (while) ---")
    print("  Формат: число оператор число (наприклад: 10 + 5)")
    print("  Введіть 'quit' для виходу в головне меню, 'history' для історії")

    history = []

    while True:
        user_input = input("\n  calc> ").strip()

        if user_input.lower() == 'quit':
            print("  Вихід з калькулятора.")
            break

        if user_input.lower() == 'history':
            print("  --- Історія обчислень ---")
            if not history:
                print("  Історія порожня.")
            else:
                for item in history:
                    print(f"    {item}")
            continue

        parts = user_input.split()
        if len(parts) != 3:
            print("  Помилка: використовуйте формат: число оператор число")
            continue

        num1_str, op, num2_str = parts

        try:
            num1 = float(num1_str)
            num2 = float(num2_str)
        except ValueError:
            print("  Помилка: числа введено некоректно.")
            continue

        result = None
        if op == '+':
            result = num1 + num2
        elif op == '-':
            result = num1 - num2
        elif op == '*':
            result = num1 * num2
        elif op == '/':
            if num2 == 0:
                print("  Помилка: ділення на нуль!")
                continue
            result = num1 / num2
        elif op == '//':
            if num2 == 0:
                print("  Помилка: цілочисельне ділення на нуль!")
                continue
            result = num1 // num2
        elif op == '%':
            if num2 == 0:
                print("  Помилка: остача від ділення на нуль!")
                continue
            result = num1 % num2
        elif op == '**':
            result = num1 ** num2
        else:
            print(f"  Помилка: невідомий оператор '{op}'. Доступні: +, -, *, /, //, %, **")
            continue

        expression_str = f"{num1} {op} {num2} = {result}"
        print(f"  Результат: {result}")
        history.append(expression_str)


# ==========================================
# ГОЛОВНЕ МЕНЮ ПРОГРАМИ
# ==========================================
def main():
    while True:
        print("\n" + "=" * 65)
        print(" ГОЛОВНЕ МЕНЮ — ПРАКТИЧНА РОБОТА №1 (Григор'євська, КБ-25)")
        print("=" * 65)
        print(" 1. Завдання 1.1 (Математичні вирази)")
        print(" 2. Завдання 1.2 (Конвертор типів та функції)")
        print(" 3. Завдання 2.1 (Класифікація оцінок ЄКТС)")
        print(" 4. Завдання 2.2 (Тип трикутника та площа)")
        print(" 5. Завдання 3.1 (Цикл for, факторіал, таблиця)")
        print(" 6. Завдання 3.2 (Інтерактивний калькулятор)")
        print(" 0. Вихід з програми")
        print("=" * 65)

        choice = input(" Оберіть номер завдання (0-6): ").strip()

        if choice == '1':
            task_1_1()
        elif choice == '2':
            task_1_2()
        elif choice == '3':
            task_2_1()
        elif choice == '4':
            task_2_2()
        elif choice == '5':
            task_3_1()
        elif choice == '6':
            task_3_2()
        elif choice == '0':
            print("\nРоботу програми завершено. До побачення!")
            break
        else:
            print("\nНевірний вибір! Будь ласка, введіть число від 0 до 6.")


if __name__ == "__main__":
    main()
