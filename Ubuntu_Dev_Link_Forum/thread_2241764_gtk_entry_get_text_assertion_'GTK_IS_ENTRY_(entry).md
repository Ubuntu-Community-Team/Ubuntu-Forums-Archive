---
title: "gtk_entry_get_text: assertion 'GTK_IS_ENTRY (entry)' failed"
date: 2014-08-28
forum: Ubuntu Dev Link Forum
---

### Post by fahedsl on 2014-08-28
Hello, I'm creating a small program with C++ and GTK 3 (just learning it), and i have had trouble with this. So, i isolated the problematic part.

It is suposed to get the entry and print it when the button is clicked.

This is the code:

```

#include <iostream>
#include <gtk/gtk.h>


using namespace std;


GtkWidget *wventana;
GtkWidget *wgrid;


//FUNCS


void ventana(string titulo, int margen)
{
    const char * tituloc = titulo.c_str();


    wventana = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position (GTK_WINDOW (wventana), GTK_WIN_POS_CENTER);
    gtk_window_set_title (GTK_WINDOW (wventana), tituloc);
    gtk_container_set_border_width(GTK_CONTAINER(wventana), margen);
}


void grid()
{
    wgrid = gtk_grid_new();
    gtk_container_add(GTK_CONTAINER(wventana), wgrid);
    gtk_grid_set_row_spacing (GTK_GRID (wgrid), 10);
    gtk_grid_set_column_spacing (GTK_GRID (wgrid), 25);
}


void boton_clic (GtkEntry *wentrada, gpointer user_data)
{
    const char *nombre;
    nombre = gtk_entry_get_text(wentrada);
    cout << nombre << endl;
}


void entrada(int x, int y, int lx, int ly)
{
    GtkWidget *wentrada;
    wentrada = gtk_entry_new();
    gtk_grid_attach (GTK_GRID (wgrid), wentrada, x, y, lx, ly);
}


void boton(string texto, int x, int y, int lx, int ly)
{
    const char * wtexto = texto.c_str();


    GtkWidget *wboton;
    wboton = gtk_button_new_with_label (wtexto);
    gtk_grid_attach (GTK_GRID (wgrid), wboton, x, y, lx, ly);


    g_signal_connect (GTK_BUTTON (wboton), "clicked", G_CALLBACK (boton_clic), G_OBJECT (wventana));
}


//MAIN


int main(int argc, char *argv[])
{
    gtk_init (&argc, &argv);


    ventana("ventana",10);
    grid();
    entrada(1, 1, 1, 1);
    boton("Aprietame", 1, 2, 1, 1);


    gtk_widget_show_all (wventana);
    gtk_main ();


    return 0;
}

```


It doesnt get the entry and shows the following error message:


```

(boton:6669): Gtk-CRITICAL **: gtk_entry_get_text: assertion 'GTK_IS_ENTRY (entry)' failed
```

Could anyone please tell what the problem is? and, how can I make it work?
Or in any case, what is a good alternative to do this? (it has to be with separated functions)

Thanks in advance.

---

