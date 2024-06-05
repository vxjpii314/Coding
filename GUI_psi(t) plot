import numpy as np
import matplotlib.pyplot as plt
import tkinter as tk
from tkinter import ttk

def compute_wavefunction():
    #const.
    lamda = float(lamda_entry.get())
    n_max = int(n_max_entry.get())
    c_n_value = float(c_n_entry.get())
    
    t = np.linspace(0, 10, 100)
    c_n = np.ones(n_max + 1) * c_n_value
    
    #wavefunction
    real = np.zeros_like(t, dtype=np.float64)
    im = np.zeros_like(t, dtype=np.float64)
    
    for n in range(n_max + 1):
        real += c_n[n] * np.cos(lamda * t * np.sqrt(n + 1))
        if n > 0:
            im += -c_n[n - 1] * np.sin(lamda * t * np.sqrt(n))
    
    psi_tot = real + 1j * im
    psi_square = np.abs(psi_tot) ** 2
    
    plt.figure()
    plt.plot(t, real, label='Graph of real part of psi vs t')
    plt.xlabel('time, t')
    plt.ylabel('Real part of psi')
    plt.title('Real part of Psi vs time')
    plt.show()
    
    plt.figure()
    plt.plot(t, psi_square, label='Graph of psi square vs t')
    plt.xlabel('time, t')
    plt.ylabel('psi square')
    plt.title('Psi square vs time')
    plt.show()

##GUI 
root = tk.Tk()
root.title("Wavefunction Visualizer")

tk.Label(root, text="Lambda:").grid(row=0, column=0)
lamda_entry = tk.Entry(root)
lamda_entry.grid(row=0, column=1)
lamda_entry.insert(0, "10")

tk.Label(root, text="n_max:").grid(row=1, column=0)
n_max_entry = tk.Entry(root)
n_max_entry.grid(row=1, column=1)
n_max_entry.insert(0, "10000")

tk.Label(root, text="c_n value:").grid(row=2, column=0)
c_n_entry = tk.Entry(root)
c_n_entry.grid(row=2, column=1)
c_n_entry.insert(0, "0.7071")

compute_button = tk.Button(root, text="Compute and Plot", command=compute_wavefunction)
compute_button.grid(row=3, columnspan=2)

root.mainloop()
