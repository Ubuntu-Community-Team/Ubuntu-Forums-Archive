---
title: "Integrating Application Indicators"
date: 2012-09-05
forum: Ubuntu Application Development
---

### Post by Conzar on 2012-09-05
I am trying to integrate Application Indicators into my FOSS project which currently uses the System Tray (its java so works in everything except Unity).  I have been searching for a tutorial on how to include Application Indicators and all I found was [this]("https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators") (seems to be outdated too).

Anyone know of a good tutorial (in the C language) that goes through the entire development process (sample C code, compile, etc)?

Thanks

UPDATE:
Source
```
#include <gtk/gtk.h>
#include <libappindicator/app-indicator.h>
 
static void activate_action (GtkAction *action);
 
static GtkActionEntry entries[] = {
  { "FileMenu", NULL, "_File" },
  { "New",      "document-new", "_New", "<control>N",
    "Create a new file", G_CALLBACK (activate_action) },
  { "Open",     "document-open", "_Open", "<control>O",
    "Open a file", G_CALLBACK (activate_action) },
  { "Save",     "document-save", "_Save", "<control>S",
    "Save file", G_CALLBACK (activate_action) },
  { "Quit",     "application-exit", "_Quit", "<control>Q",
    "Exit the application", G_CALLBACK (gtk_main_quit) },
};
static guint n_entries = G_N_ELEMENTS (entries);
 
static const gchar *ui_info =
"<ui>"
"  <menubar name='MenuBar'>"
"    <menu action='FileMenu'>"
"      <menuitem action='New'/>"
"      <menuitem action='Open'/>"
"      <menuitem action='Save'/>"
"      <separator/>"
"      <menuitem action='Quit'/>"
"    </menu>"
"  </menubar>"
"  <popup name='IndicatorPopup'>"
"    <menuitem action='New' />"
"    <menuitem action='Open' />"
"    <menuitem action='Save' />"
"    <menuitem action='Quit' />"
"  </popup>"
"</ui>";
 
static void
activate_action (GtkAction *action)
{
        const gchar *name = gtk_action_get_name (action);
        GtkWidget *dialog;
 
        dialog = gtk_message_dialog_new (NULL,
                                         GTK_DIALOG_DESTROY_WITH_PARENT,
                                         GTK_MESSAGE_INFO,
                                         GTK_BUTTONS_CLOSE,
                                         "You activated action: \"%s\"",
                                         name);
 
        g_signal_connect (dialog, "response",
                          G_CALLBACK (gtk_widget_destroy), NULL);
 
        gtk_widget_show (dialog);
}
 
int main (int argc, char **argv)
{
  GtkWidget *window;
  GtkWidget *menubar;
  GtkWidget *table;
  GtkWidget *sw;
  GtkWidget *contents;
  GtkWidget *statusbar;
  GtkWidget *indicator_menu;
  GtkActionGroup *action_group;
  GtkUIManager *uim;
  AppIndicator *indicator;
  GError *error = NULL;
 
  gtk_init (&argc, &argv);
 
  /* main window */
  window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_window_set_title (GTK_WINDOW (window), "Indicator Demo");
  gtk_window_set_icon_name (GTK_WINDOW (window), "indicator-messages-new");
  g_signal_connect (G_OBJECT (window),
                    "destroy",
                    G_CALLBACK (gtk_main_quit),
                    NULL);
 
  table = gtk_table_new (1, 5, FALSE);
  gtk_container_add (GTK_CONTAINER (window), table);
 
  /* Menus */
  action_group = gtk_action_group_new ("AppActions");
  gtk_action_group_add_actions (action_group,
                                entries, n_entries,
                                window);
 
  uim = gtk_ui_manager_new ();
  g_object_set_data_full (G_OBJECT (window),
                          "ui-manager", uim,
                          g_object_unref);
  gtk_ui_manager_insert_action_group (uim, action_group, 0);
  gtk_window_add_accel_group (GTK_WINDOW (window),
                              gtk_ui_manager_get_accel_group (uim));
 
  if (!gtk_ui_manager_add_ui_from_string (uim, ui_info, -1, &error))
    {
      g_message ("Failed to build menus: %s\n", error->message);
      g_error_free (error);
      error = NULL;
    }
 
  menubar = gtk_ui_manager_get_widget (uim, "/ui/MenuBar");
  gtk_widget_show (menubar);
  gtk_table_attach (GTK_TABLE (table),
                    menubar,
                    0, 1,                    0, 1,
                    GTK_EXPAND | GTK_FILL,   0,
                    0,                       0);
 
  /* Document */
  sw = gtk_scrolled_window_new (NULL, NULL);
 
  gtk_scrolled_window_set_policy (GTK_SCROLLED_WINDOW (sw),
                                  GTK_POLICY_AUTOMATIC,
                                  GTK_POLICY_AUTOMATIC);
 
  gtk_scrolled_window_set_shadow_type (GTK_SCROLLED_WINDOW (sw),
                                       GTK_SHADOW_IN);
 
  gtk_table_attach (GTK_TABLE (table),
                    sw,
                    /* X direction */       /* Y direction */
                    0, 1,                   3, 4,
                    GTK_EXPAND | GTK_FILL,  GTK_EXPAND | GTK_FILL,
                    0,                      0);
 
  gtk_window_set_default_size (GTK_WINDOW (window),
                               200, 200);
 
  contents = gtk_text_view_new ();
  gtk_widget_grab_focus (contents);
 
  gtk_container_add (GTK_CONTAINER (sw),
                     contents);
 
  /* Create statusbar */
  statusbar = gtk_statusbar_new ();
  gtk_table_attach (GTK_TABLE (table),
                    statusbar,
                    /* X direction */       /* Y direction */
                    0, 1,                   4, 5,
                    GTK_EXPAND | GTK_FILL,  0,
                    0,                      0);
 
  /* Show the window */
  gtk_widget_show_all (window);
 
  /* Indicator */
  indicator = app_indicator_new ("example-simple-client",
                                 "indicator-messages",
                                 APP_INDICATOR_CATEGORY_APPLICATION_STATUS);
 
  indicator_menu = gtk_ui_manager_get_widget (uim, "/ui/IndicatorPopup");
 
  app_indicator_set_status (indicator, APP_INDICATOR_STATUS_ACTIVE);
  app_indicator_set_attention_icon (indicator, "indicator-messages-new");
 
  app_indicator_set_menu (indicator, GTK_MENU (indicator_menu));
 
  gtk_main ();
 
  return 0;
}
```
Compile
```
gcc example.c `pkg-config --cflags gtk+-2.0` -I/usr/include/libappindicator-0.1/  -o example `pkg-config --libs gtk+-2.0` -L/usr/lib -lappindicator

```

---

### Post by mhall119 on 2012-09-08
[http://developer.ubuntu.com/resources/technologies/application-indicators/](http://developer.ubuntu.com/resources/technologies/application-indicators/) has documentation and code examples for creating an application indicator for your app.

---

### Post by Conzar on 2012-09-09
> **mhall119 said:**
> [http://developer.ubuntu.com/resources/technologies/application-indicators/](http://developer.ubuntu.com/resources/technologies/application-indicators/) has documentation and code examples for creating an application indicator for your app.

Thanks. Its a good coding example; however, how is it supposed to be compiled?

The following doesn't work:
```
gcc example.c 
example.c:1:43: fatal error: libappindicator/app-indicator.h: No such file or directory
compilation terminated.

```

Thanks

---

### Post by mhall119 on 2012-09-09
Sorry, I'm a python guy, not really sure what's needed to get C code compiling

---

### Post by Conzar on 2012-09-09
> **mhall119 said:**
> Sorry, I'm a python guy, not really sure what's needed to get C code compiling

Thanks for your help though.  I primarily code in Java but do some C/C++ when required.  Compiling C system libraries is a nightmare to figure out if there is no documentation on how to do it or at least a Make file.  

Anyone else know how do to this?  How are developers expected to use Application Indicators if the documentation isn't complete?

---

### Post by Conzar on 2012-09-10
From this [Q&A]("http://stackoverflow.com/questions/6016815/how-to-include-needed-c-library-using-gcc") it was suggested to do the following:
```
gcc -I/usr/include/libappindicator-0.1/libappindicator/ example.c
```

However, I get the following output:
```
example.c:1:43: fatal error: libappindicator/app-indicator.h: No such file or directory
compilation terminated.
```

Note, I have libappindictaor-dev package installed as shown below:
```
l /usr/include/libappindicator-0.1/libappindicator/
app-indicator-enum-types.h  app-indicator.h
```

Anyone know what how I can fix this?

---

### Post by Conzar on 2012-09-10
Found a solution:
```
gcc -I/usr/include/libappindicator-0.1/ example.c In file included from example.c:1:0:
/usr/include/libappindicator-0.1/libappindicator/app-indicator.h:33:21: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.

```
Now I just need to link to the gtk library...

After finding another [resource]("http://developer.gnome.org/gtk-tutorial/2.22/x111.html"): I get this

```
gcc `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0` -I/usr/include/libappindicator-0.1/ example.c
/tmp/ccBOtoqx.o: In function `activate_action':
example.c:(.text+0x14): undefined reference to `gtk_action_get_name'
example.c:(.text+0x43): undefined reference to `gtk_message_dialog_new'
example.c:(.text+0x4c): undefined reference to `gtk_widget_destroy'
example.c:(.text+0x6e): undefined reference to `g_signal_connect_data'
example.c:(.text+0x7a): undefined reference to `gtk_widget_show'
/tmp/ccBOtoqx.o: In function `main':
example.c:(.text+0xaa): undefined reference to `gtk_init'
example.c:(.text+0xb4): undefined reference to `gtk_window_new'
example.c:(.text+0xbd): undefined reference to `gtk_window_get_type'
example.c:(.text+0xcf): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0xdc): undefined reference to `gtk_window_set_title'
example.c:(.text+0xe1): undefined reference to `gtk_window_get_type'
example.c:(.text+0xf3): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x100): undefined reference to `gtk_window_set_icon_name'
example.c:(.text+0x111): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x127): undefined reference to `gtk_main_quit'
example.c:(.text+0x134): undefined reference to `g_signal_connect_data'
example.c:(.text+0x148): undefined reference to `gtk_table_new'
example.c:(.text+0x151): undefined reference to `gtk_container_get_type'
example.c:(.text+0x163): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x172): undefined reference to `gtk_container_add'
example.c:(.text+0x17c): undefined reference to `gtk_action_group_new'
example.c:(.text+0x19b): undefined reference to `gtk_action_group_add_actions'
example.c:(.text+0x1a0): undefined reference to `gtk_ui_manager_new'
example.c:(.text+0x1b5): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x1be): undefined reference to `g_object_unref'
example.c:(.text+0x1cb): undefined reference to `g_object_set_data_full'
example.c:(.text+0x1e3): undefined reference to `gtk_ui_manager_insert_action_group'
example.c:(.text+0x1ef): undefined reference to `gtk_ui_manager_get_accel_group'
example.c:(.text+0x1f7): undefined reference to `gtk_window_get_type'
example.c:(.text+0x209): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x214): undefined reference to `gtk_window_add_accel_group'
example.c:(.text+0x235): undefined reference to `gtk_ui_manager_add_ui_from_string'
example.c:(.text+0x25d): undefined reference to `g_log'
example.c:(.text+0x269): undefined reference to `g_error_free'
example.c:(.text+0x282): undefined reference to `gtk_ui_manager_get_widget'
example.c:(.text+0x292): undefined reference to `gtk_widget_show'
example.c:(.text+0x297): undefined reference to `gtk_table_get_type'
example.c:(.text+0x2a9): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x2ea): undefined reference to `gtk_table_attach'
example.c:(.text+0x2f9): undefined reference to `gtk_scrolled_window_new'
example.c:(.text+0x302): undefined reference to `gtk_scrolled_window_get_type'
example.c:(.text+0x314): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x326): undefined reference to `gtk_scrolled_window_set_policy'
example.c:(.text+0x32b): undefined reference to `gtk_scrolled_window_get_type'
example.c:(.text+0x33d): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x34a): undefined reference to `gtk_scrolled_window_set_shadow_type'
example.c:(.text+0x34f): undefined reference to `gtk_table_get_type'
example.c:(.text+0x361): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x3a2): undefined reference to `gtk_table_attach'
example.c:(.text+0x3a7): undefined reference to `gtk_window_get_type'
example.c:(.text+0x3b9): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x3cb): undefined reference to `gtk_window_set_default_size'
example.c:(.text+0x3d0): undefined reference to `gtk_text_view_new'
example.c:(.text+0x3e0): undefined reference to `gtk_widget_grab_focus'
example.c:(.text+0x3e5): undefined reference to `gtk_container_get_type'
example.c:(.text+0x3f7): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x406): undefined reference to `gtk_container_add'
example.c:(.text+0x40b): undefined reference to `gtk_statusbar_new'
example.c:(.text+0x414): undefined reference to `gtk_table_get_type'
example.c:(.text+0x426): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x467): undefined reference to `gtk_table_attach'
example.c:(.text+0x473): undefined reference to `gtk_widget_show_all'
example.c:(.text+0x487): undefined reference to `app_indicator_new'
example.c:(.text+0x49c): undefined reference to `gtk_ui_manager_get_widget'
example.c:(.text+0x4b1): undefined reference to `app_indicator_set_status'
example.c:(.text+0x4c2): undefined reference to `app_indicator_set_attention_icon'
example.c:(.text+0x4c7): undefined reference to `gtk_menu_get_type'
example.c:(.text+0x4d9): undefined reference to `g_type_check_instance_cast'
example.c:(.text+0x4eb): undefined reference to `app_indicator_set_menu'
example.c:(.text+0x4f0): undefined reference to `gtk_main'
/tmp/ccBOtoqx.o:(.data+0xe8): undefined reference to `gtk_main_quit'
collect2: ld returned 1 exit status
```

---

### Post by Conzar on 2012-09-10
Two steps closer to a working example:

Compile line
```
gcc example.c `pkg-config --cflags gtk+-2.0` -I/usr/include/libappindicator-0.1/  -o example `pkg-config --libs gtk+-2.0`

```

In the source added the following:
```
#include <gtk/gtk.h>

```

---

### Post by Conzar on 2012-09-10
I finially built it!!!!

```
gcc example.c `pkg-config --cflags gtk+-2.0` -I/usr/include/libappindicator-0.1/  -o example `pkg-config --libs gtk+-2.0` -L/usr/lib -lappindicator

```

---

