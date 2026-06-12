---
title: "How to write a GTK+ application with a menu in the titlebar?"
date: 2016-10-24
forum: Ubuntu Application Development
---

### Post by dkdk on 2016-10-24
Hi,

I'm writing an application in C++ with a gui in GTK+. I use Ubuntu 16.10 and windows menus are integrated in the title bar. For example, here is GHex (an hexadecimal viewer):
[IMG]http://i.imgur.com/i01OEPm.png[/IMG]

But with my code, the menu is displayed below the titlebar:
[IMG]http://i.imgur.com/ltn1qcN.png[/IMG]

Here is my code. How should I update it to get the menu integrated?

```

#include <gtk/gtk.h>

int main(int argc, char** argv) {

    gtk_init(&argc, &argv);

    auto window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
    gtk_window_set_default_size(GTK_WINDOW(window), 320, 200);
    gtk_window_set_title(GTK_WINDOW(window), "MyApp");

    auto vbox = gtk_box_new(GTK_ORIENTATION_VERTICAL, 0);

    auto menubar = gtk_menu_bar_new();
    auto file_menu = gtk_menu_new();
    auto file_menu_item = gtk_menu_item_new_with_label("File");
    auto quit_menu_item = gtk_menu_item_new_with_label("Quit");

    gtk_menu_item_set_submenu(GTK_MENU_ITEM(file_menu_item), file_menu);
    gtk_menu_shell_append(GTK_MENU_SHELL(file_menu), quit_menu_item);
    gtk_menu_shell_append(GTK_MENU_SHELL(menubar), file_menu_item);
    gtk_box_pack_start(GTK_BOX(vbox), menubar, FALSE, FALSE, 0);

    gtk_container_add(GTK_CONTAINER(window), vbox);
    
    g_signal_connect(G_OBJECT(window),
        "destroy", G_CALLBACK(gtk_main_quit), nullptr);

    g_signal_connect(G_OBJECT(quit_menu_item),
        "activate", G_CALLBACK(gtk_main_quit), nullptr);

    gtk_widget_show_all(window);
    gtk_main();
    return 0;
}

```

The Makefile:
```

FLAGS := $(shell pkg-config --cflags gtk+-3.0)
LIBS := $(shell pkg-config --libs gtk+-3.0)

all: a.out
a.out:
	g++ -std=c++11 $(FLAGS) menu.cpp $(LIBS)
run: a.out
	./$<

```

---

### Post by dkdk on 2016-11-13
I tested today and my menu is now located in the title bar, as expected. I guess something was broken in Ubuntu 16.10 and it was repaired during an upgrade.

---

