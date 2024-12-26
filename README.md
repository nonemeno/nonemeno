import time

dataset = {
    "multiplier": 0.1,
    "inventory": ["boosting 0.45"],
    "store": {
        "monster": 0.10  # цена на 10 секунд
    },
    "balance": 0
}

def print_banner():
    print("""
               .:-==+=.            
..::--::.  .=++++==-::             
-==---..:**#:                      
         -*-                       
         =#:                       
         +#.                       
         *#                        
        .#*                        
        .#=                        
        .+-                        
        :*:                        
        =%                         
        *#                         
        #*                         
       .%=                         
       :%-                         
       =%:                         
       #%*                         
      .%%:                         
      -#%:                     .:. 
      +%%#+.                ..+###-
      #%+-*#+.   ..::::-==+++****#+
     =%%+  ##%*+++++++*++==-:..:=- 
    +#%%#  .=++==-:..              
          """)

def tap_scooter():
    global tap_count
    input("Нажмите Enter, чтобы тапнуть самокат")
    tap_count += 1
    print(f"Текущий счёт: {tap_count}")

def show_inventory():
    print("Ваш инвентарь:")
    for item in dataset["inventory"]:
        print(f"- {item}")

def show_store():
    print("Магазин:")
    for item, price in dataset["store"].items():
        print(f"- {item}: {price} монет")

def buy_item():
    show_store()
    item = input("Введите название предмета, который хотите купить: ")
    if item not in dataset["store"]:
        print(f"Предмет '{item}' отсутствует в магазине.")
        return
    
    price = dataset["store"][item]
    if dataset["balance"] < price:
        print("Недостаточно средств для покупки этого предмета.")
        return
    
    dataset["balance"] -= price
    dataset["inventory"].append(item)
    print(f"Покупка завершена! Предмет '{item}' добавлен в ваш инвентарь.")

def use_boost():
    boost_time = 10  # время действия усиления в секундах
    print(f"Усиление включено на {boost_time} секунд...")
    time.sleep(boost_time)  # имитируем задержку во времени
    print("Усиление закончилось.")

def show_statistics():
    print("Статистика:")
    print(f"Счёт: {tap_count}")
    print(f"Баланс: {dataset['balance']} монет")

def main():
    global tap_count
    tap_count = 0

    print("Создайте своего стрит скуфа!")
    age = input("Сколько лет? ")
    height = input("Рост? ")
    weight = input("Вес? ")
    print("\nИгра начинается!")

    while True:
        print("\nВыберите действие:")
        print("1 - Тапать самокат")
        print("2 - Инвентарь")
        print("3 - Магазин")
        print("4 - Статистика")
        print("5 - Купить предмет")
        print("6 - Выход")

        choice = input("Ваш выбор: ")

        if choice == "1":
            tap_scooter()
        elif choice == "2":
            show_inventory()
        elif choice == "3":
            show_store()
        elif choice == "4":
            show_statistics()
        elif choice == "5":
            buy_item()
        elif choice == "6":
            print("Спасибо за игру!")
            break
        else:
            print("Некорректный выбор. Попробуйте снова.")

if __name__ == "__main__":
    main()
