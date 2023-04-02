# Pirates-Vs-Ninjas
Assignment: Object Oriented Programming
/*
Sanyerlis Camacaro- CSC275 - Sancamac@uat.edu
Assignment: Object Oriented Programming
To Declare variables using appropriate data-types & scope.
To Derive new classes from base classes and abstract classes.
To Use polymorphism in applications.
Create a Project called Pirate Vs. Ninjas.
*/

#include <iostream> // includes input and out as the standard library.
#include <string> //this allows me to work with strings.
using namespace std; // means using standard namespace and that I dont have to type std:: in front of each line.

// GameStructure class
class GameStructure {
public:
    virtual void Help() = 0; // Pure virtual method
};

// Character class inheriting from GameStructure
class Character : public GameStructure {
public:
    string Name;

    // Getter and setter for private Health property
    int GetHealth() {
        return Health;
    }

    void SetHealth(int newHealth) {
        if (newHealth < 0) {
            Health = 0;
            cout << "Character has Expired..." << endl;
        }
        else {
            Health = newHealth;
        }
    }

    // Overloaded Talk methods
    void Talk(string stuffToSay) {
        cout << Name << ": " << stuffToSay << endl;
    }

    void Talk(string name, string stuffToSay) {
        cout << name << ": " << stuffToSay << endl;
    }

    // Virtual attack method
    virtual int Attack() {
        return 10;
    }

    // Overriding Help method
    void Help() override {}

protected:
    int Health;

};

// Ninja class inheriting from Character
class Ninja : public Character {
public:
    Ninja() {
        Name = "Ninja";
        Health = 100;
    }
    // Overriding ThrowStars method
    void ThrowStars() {
        cout << "I am throwing stars!" << endl;
    }

    // Overriding Attack method
    int Attack() override {
        cout << "You lost 25 health points" << endl;
        return 25;
    }

    // Overriding Help method
    void Help() override {
        cout << "Ninja's are really cool, can you can use them to throw stars!" << endl;
    }
};

// Pirate class inheriting from Character
class Pirate : public Character {
public:
    Pirate() {
        Name = "Pirate";
        Health = 100;
    }
    // Overriding UseSword method
    void UseSword() {
        cout << "I am Swooshing my Sword!" << endl;
    }

    // Overriding Attack method
    int Attack() override {
        cout << "You lost 25 health points" << endl;
        return 25;
    }

    // Overriding Help method
    void Help() override {
        cout << "Pirates are fearsome fighters, you can use them to swoosh their swords!" << endl;
    }
};

// Main function
int main() {
    cout << "Welcome to the Pirates vs Ninjas Game!" << endl;
    cout << "Choose your character and fight for Victory!" << endl;

    Ninja ninja;
    Pirate pirate;

    bool keepPlaying = true;
    int choice;

    // Menu
    while (keepPlaying) {
        cout << "\nChoose an action:\n";
        cout << "1. Throw Stars (Ninja)\n";
        cout << "2. Use Sword (Pirate)\n";
        cout << "3. Get Help (Ninja)\n";
        cout << "4. Get Help (Pirate)\n";
        cout << "5. Attack (Ninja)\n";
        cout << "6. Attack (Pirate)\n";
        cout << "7. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        // Actions after making a selection from menu.
        switch (choice) {
        case 1:
            ninja.ThrowStars();
            break;
        case 2:
            pirate.UseSword();
            break;
        case 3:
            ninja.Help();
            break;
        case 4:
            pirate.Help();
            break;
        case 5:
            ninja.Attack();
            break;
        case 6:
            pirate.Attack();
            break;
        case 7:
            keepPlaying = false;
            break;
        default:
            cout << "Invalid choice, try again." << endl;
        }
    }

    cout << "Thanks for playing!" << endl;
    return 0;
}
