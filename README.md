# Stock Portfolio Tracker

# Hardcoded stock prices
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOGL": 140,
    "MSFT": 420,
    "AMZN": 190
}

portfolio = {}
total_value = 0

print("===== Stock Portfolio Tracker =====")

while True:
    stock = input("Enter Stock Symbol (or 'done' to finish): ").upper()

    if stock == "DONE":
        break

    if stock not in stock_prices:
        print("Stock not available!")
        continue

    quantity = int(input(f"Enter quantity for {stock}: "))

    portfolio[stock] = quantity

# Calculate total investment value
print("\n===== Portfolio Summary =====")

for stock, quantity in portfolio.items():
    value = stock_prices[stock] * quantity
    total_value += value

    print(
        f"{stock} | Quantity: {quantity} | Price: ${stock_prices[stock]} | Value: ${value}"
    )

print(f"\nTotal Investment Value: ${total_value}")

# Save to file
with open("portfolio_report.txt", "w") as file:
    file.write("Stock Portfolio Report\n")
    file.write("=======================\n")

    for stock, quantity in portfolio.items():
        value = stock_prices[stock] * quantity
        file.write(
            f"{stock} | Quantity: {quantity} | Price: ${stock_prices[stock]} | Value: ${value}\n"
        )

    file.write(f"\nTotal Investment Value: ${total_value}")

print("\nPortfolio report saved as 'portfolio_report.txt'")
