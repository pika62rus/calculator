# calculator

def calculator(expression):
    """
    Evaluates a mathematical expression with two integers and an operator.

    Args:
        expression (str): A string containing two numbers and an operator, e.g. "2+3"

    Returns:
        int: The result of the operation

    Raises:
        ValueError: If the input is invalid (non-integer numbers, numbers out of range, or invalid operator)
    """
    try:
        # Check if the input string contains exactly one operator
        if sum(expression.count(op) for op in "+-*/") != 1:
            raise ValueError("Invalid operator")

        # Split the input string into two numbers and an operator
        for op in "+-*/":
            if op in expression:
                a, b = expression.split(op)
                break

        # Convert the numbers to integers
        a, b = int(a), int(b)

        # Check if the numbers are within the range of 1 to 10
        if not (1 <= a <= 10 and 1 <= b <= 10):
            raise ValueError("Numbers must be between 1 and 10")

        # Perform the operation
        if op == "+":
            return a + b
        elif op == "-":
            return a - b
        elif op == "*":
            return a * b
        elif op == "/":
            if b == 0:
                raise ValueError("Division by zero is not allowed")
            return a // b  # Use integer division (//) to discard remainder
    except ValueError as e:
        print(f"Error: {e}")
        exit(1)
