---
title: "GTK: Expected 'struct GtkSwitch *' but argument is of type 'struct GtkWidget *'"
date: 2014-12-09
forum: Ubuntu Application Development
---

### Post by jusaca on 2014-12-09
I'm an electronics engineer and can't program very good, but in my current project I need to program a little GUI.
So I read about GTK+ and at the moment I'm learning a lot about this stuff.
But I have a problem and can't find a solution for myself, so i decided to ask in this forum ;)

In my code I create a switch, place it in a grid of a window and try to ask for the value with:

```

GtkWidget *schalter1;
schalter1 = gtk_switch_new();
gtk_grid_attach(GTK_GRID(grid), schalter1, 0,1,2,1);

if (gtk_switch_get_active(schalter1))
{
       gtk_widget_set_sensitive (button, FALSE);
}

```

I get this warning:
"Passing argument 1 of gtk_switch_get_active from incompatible pointer type [enable by default]
Expected 'struct GtkSwitch *' but argument is of type 'struct GtkWidget *'"
The switch is in the right position, but I can't change the sensitive-state of the button

When I change GtkWidget in the Code to GtkSwitch, the warning turns around:
The gtk_grid_attach expects a GtkWidget...

Can anybody explain to me what I have to code to make this work?
Please remember, I'm new to programing and are just learning by doing^^

Greets
jusaca

---

