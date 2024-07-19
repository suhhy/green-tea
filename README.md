# green-tea
import tkinter as tk
from tkinter import ttk, messagebox

# Описания чаев
tea_descriptions = {
    "Зеленый чай": "Зеленый чай известен своими антиоксидантными свойствами и легким вкусом.",
    "Черный чай": "Черный чай обладает насыщенным вкусом и высоким содержанием кофеина.",
    "Белый чай": "Белый чай – это мягкий и деликатный напиток с легким вкусом.",
    "Улун чай": "Улун чай сочетает в себе лучшие качества зеленого и черного чая.",
    "Травяной чай": "Травяной чай не содержит кофеина и может включать различные травы и специи."
}

def show_description(event):
    selected_tea = tea_combo.get()
    if selected_tea in tea_descriptions:
        description = tea_descriptions[selected_tea]
        description_label.config(text=description)
    else:
        messagebox.showerror("Ошибка", "Выбранный тип чая недоступен")
        description_label.config(text="")

# Создаем главное окно
root = tk.Tk()
root.title("Выбор чая")
root.geometry("400x300")

# Надпись и выпадающий список для выбора чая
tea_label = tk.Label(root, text="Выберите тип чая:")
tea_label.pack(pady=10)

tea_combo = ttk.Combobox(root, values=list(tea_descriptions.keys()))
tea_combo.pack(pady=10)
tea_combo.bind("<<ComboboxSelected>>", show_description)

# Надпись для отображения описания чая
description_label = tk.Label(root, text="", wraplength=300)
description_label.pack(pady=20)

# Запуск главного цикла обработки событий
root.mainloop()
