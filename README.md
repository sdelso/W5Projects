guess.py
import math
def computer_guess():
    print("Think of a number between a lower and upper bound, and I'll try to guess it!")
    lower = int(input("Enter the lower bound: "))
    upper = int(input("Enter the upper bound: "))
    if lower >= upper:
        print("Invalid bounds. The lower bound must be less than the upper bound.")
        return
    max_guesses = math.ceil(math.log2(upper - lower + 1))
    print(f"I will guess your number in at most {max_guesses} tries.")
    attempts = 0
    while lower <= upper:
        guess = (lower + upper) // 2
        print(f"Is your number {guess}? (enter 'h' if higher, 'l' if lower, 'c' if correct)")
        response = input().strip().lower()
        if response == 'c':
            attempts += 1
            print(f"Yay! I guessed your number in {attempts} attempts.")
            break
        elif response == 'h':
            lower = guess + 1
        elif response == 'l':
            upper = guess - 1
        else:
            print("Invalid response. Please enter 'h', 'l', or 'c'.")
            continue
        attempts += 1
        if attempts > max_guesses:
            print("You're cheating! The number of guesses exceeded the expected limit.")
            break
    else:
        print("Something went wrong. Make sure you are responding correctly!")
if __name__ == "__main__":
    computer_guess()

salary.py
def salary_schedule():
    print("Salary Schedule Calculator")
    starting_salary = float(input("Enter the starting salary: "))
    percentage_increase = float(input("Enter the annual percentage increase: "))
    years = int(input("Enter the number of years in the schedule: "))
    print("\nYear\tSalary")
    print("-------------------")
    salary = starting_salary
    for year in range(1, years + 1):
        print(f"{year}\t${salary:,.2f}")
        salary += salary * (percentage_increase / 100)
if __name__ == "__main__":
    salary_schedule()

tidbit.py
def tidbit_payment_schedule():
    print("TidBit Computer Store Credit Plan")
    
    purchase_price = float(input("Enter the purchase price: "))
    down_payment = purchase_price * 0.10
    annual_interest_rate = 0.12
    monthly_payment = (purchase_price - down_payment) * 0.05
    balance = purchase_price - down_payment
    
    print("\nMonth\tBalance Owed\tInterest\tPrincipal\tPayment\tRemaining Balance")
    print("----------------------------------------------------------------------------------")
    
    month = 0
    while balance > 0:
        month += 1
        interest = balance * (annual_interest_rate / 12)
        principal = monthly_payment - interest
        
        if balance < monthly_payment:
            monthly_payment = balance + interest
            principal = balance
        
        remaining_balance = balance - principal
        
        print(f"{month}\t${balance:,.2f}\t${interest:,.2f}\t${principal:,.2f}\t${monthly_payment:,.2f}\t${remaining_balance:,.2f}")
        
        balance = remaining_balance
    
if __name__ == "__main__":
    tidbit_payment_schedule()
