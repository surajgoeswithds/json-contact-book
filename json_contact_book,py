import json #comments written on JSON part for revision as i am new to this json part
import os # os handles operating system stuff — files, folders, paths. os.path.exists() is the specific tool that checks "does this file exist on disk right now?" Without os, your load_contacts() would crash on first run because it would try to read a file that doesn't exist yet.

CONTACTS_FILE = "contacts.json" 

def load_contacts():
    if not os.path.exists(CONTACTS_FILE):   #os.path.exists(CONTACTS_FILE) Checks if the file contacts.json actually exists on your disk. First time you run the program, the file doesn't exist yet. Without this check, open() would crash trying to read a file that isn't there. It returns True or False.
        return [] #return [] If the file doesn't exist, there are no contacts yet. So return an empty list — meaning "start fresh, zero contacts." Square brackets = empty list.
    with open(CONTACTS_FILE, "r") as f:
        return json.load(f) #json.load(f) Your file has text that looks like this: [{"name": "Raj", "phone": "9876543210"}]. json.load() converts that text into an actual Python list of dictionaries you can work with. Without it, you'd just have a raw string.

def save_contacts(contacts):
    with open(CONTACTS_FILE, "w") as f:
        json.dump(contacts, f, indent=4) #json.dump(contacts, f, indent=4) Opposite of json.load(). Takes your Python list of dictionaries and converts it to text and writes it into the file. indent=4 just makes it readable with proper spacing instead of one ugly long line.


def search_contact(contacts , name):
    for contact in contacts:
        if contact["name"] == name:
            return contact

        
def add_contacts(contacts):
    cont_name=input("enter the full name:  ")
    cont_number=input("enter the number: ")

    contact_dict={
        "name" : cont_name ,
        "phone" : cont_number
    }

    contacts.append(contact_dict)
    save_contacts(contacts)


def delete_contact(contacts1 , name):
    for contact in contacts1:
        if contact["name"] == name:
            contacts1.remove(contact)
            save_contacts(contacts1)


def list_all_contacts(contacts):
    for contact in contacts: 
         print(contact['name'] , contact['phone'])

contacts = load_contacts()

while True:
    print("1. Add contact")
    print("2. Search contact")
    print("3. Delete contact")
    print("4. List all contacts")
    print("5. Quit")
    choice = input("pick one option from here:")
    if choice == "1":
        add_contacts(contacts)    
    if choice == "2":
        choice1 = input("pick a name to search:")
        search_contact(contacts , choice1)
    if choice == "3":
        choice2 = input("pick name to delete:")
        delete_contact(contacts , choice2)
    if choice == "4":
        list_all_contacts(contacts)
    if choice == "5":
        break

