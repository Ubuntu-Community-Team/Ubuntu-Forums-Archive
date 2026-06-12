---
title: "Weird Ubuntu 9.04 gtkFileChooser dialog bug??"
date: 2009-06-07
forum: Ubuntu Dev Link Forum
---

### Post by Dacobi on 2009-06-07
Hello List

I'm struggling with a gtk bug that I don't know if is ubuntu specific
but i suspect it is.

In my app when I open a file chooser dialog the dialog will freeze with
an hourglass and home folder and desktop icons are missing from the left
pane.

If I take the same open dialog code and compile in a small test app it
works.

A user on the gtk list thinks that its related to linking of libgio.

I link my app with gtk, gtksourcview1, gtkglext1, glew, opengl, openal,
sdl, libxml and others.

How do I fix it?
What could be the bug?

This is the code I use which works as a simple hello world app:

-------------------------------------

#include <gtk/gtk.h>

void
hello (void)
{
g_print ("Hello World\n");
}

void
destroy (void)
{
gtk_main_quit ();
}

void opendialog(void){
GtkWidget *filedialog;

filedialog = gtk_file_chooser_dialog_new ("Open File", NULL,
GTK_FILE_CHOOSER_ACTION_OPEN,
GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL, GTK_STOCK_OPEN,
GTK_RESPONSE_ACCEPT, NULL);

GtkFileFilter *filter;
filter = gtk_file_filter_new();

gtk_file_filter_add_pattern(filter, "*.xml");

gtk_file_chooser_set_filter(GTK_FILE_CHOOSER(filed ialog), filter);


if (gtk_dialog_run (GTK_DIALOG (filedialog)) == GTK_RESPONSE_ACCEPT)
{
char *filename;

filename = gtk_file_chooser_get_filename (GTK_FILE_CHOOSER
(filedialog));
g_free (filename);
}

gtk_widget_destroy(filedialog);

}


main (int argc, char *argv[])
{
GtkWidget *window;
GtkWidget *button;

gtk_init (&argc, &argv);

window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
gtk_signal_connect (GTK_OBJECT (window), "destroy",
GTK_SIGNAL_FUNC (destroy), NULL);
gtk_container_border_width (GTK_CONTAINER (window), 10);

button = gtk_button_new_with_label ("Hello World");

gtk_signal_connect (GTK_OBJECT (button), "clicked",
GTK_SIGNAL_FUNC (opendialog), NULL);
gtk_signal_connect_object (GTK_OBJECT (button), "clicked",
hello,
GTK_OBJECT (window));
gtk_container_add (GTK_CONTAINER (window), button);
gtk_widget_show (button);

gtk_widget_show (window);

gtk_main ();

return 0;
}

---

