# exceptions
#include <iostream>
#include <stdexcept>
#include <string>

int main() {
    try {
        std::string input1, input2;
        double num1, num2;
        
        std::cout << "Введите первое число: ";
        std::cin >> input1;
        std::cout << "Введите второе число: ";
        std::cin >> input2;

        // Попытка преобразовать строки в числа
        try {
            num1 = std::stod(input1);
            num2 = std::stod(input2);
        } catch (const std::invalid_argument&) {
            throw std::invalid_argument("Введены некорректные данные. Пожалуйста, введите числа.");
        }

        // Проверка деления на ноль
        if (num2 == 0) {
            throw std::runtime_error("Деление на ноль невозможно!");
        }

        double result = num1 / num2;
        std::cout << "Результат деления: " << result << std::endl;

    } catch (const std::runtime_error& e) {
        std::cerr << "Ошибка выполнения: " << e.what() << std::endl;
    } catch (const std::invalid_argument& e) {
        std::cerr << "Ошибка ввода: " << e.what() << std::endl;
    } catch (...) {
        std::cerr << "Произошла неизвестная ошибка!" << std::endl;
    }

    return 0;
}
