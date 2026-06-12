---
title: "gtk_file_chooser_set_show_hidden not working"
date: 2009-10-09
forum: Ubuntu Dev Link Forum
---

### Post by froggyswamp on 2009-10-09
Folks, does anyone know why despite setting to show hidden files the dialog still doesn't show them?

```

#include <gtk/gtk.h>

int main(int argc, char **argv) {
	GtkWidget *dialog;
	gint result;
	
	gtk_init(&argc, &argv);
	
	dialog = gtk_file_chooser_dialog_new("Create a Folder...", NULL,
		GTK_FILE_CHOOSER_ACTION_CREATE_FOLDER,
		GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL,
		GTK_STOCK_SAVE, GTK_RESPONSE_OK,
		NULL);
	
	//next line tells to show hidden files & folders
	gtk_file_chooser_set_show_hidden(GTK_FILE_CHOOSER(dialog), TRUE);
	result = gtk_dialog_run(GTK_DIALOG(dialog));
	gtk_widget_destroy(dialog);
	return 0;
}

```

Sorry this should go to programming talk, can anyone move it please?

---

### Post by edscott on 2011-05-23
Been a while since you asked your question, and I ran into the same problem while working on a fast multithreading filemanager ([http://rodent.xffm.org](http://rodent.xffm.org)). The only detail is that your code does show hidden files, mine did not. I suppose you stumbled on a gtk bug that was quickly fixed, but not completely fixed.

The difference: I was setting the current folder with gtk_file_chooser_set_current_folder().

Apparently if you set the current folder to a non-hidden directory with gtk_file_chooser_set_current_folder(), there is no way that gtk will show hidden files. This is with gtk 2.22.1

The fix? Just don't use gtk_file_chooser_set_current_folder() if you want to show hidden files. Yeah, I know it is not pretty, but it solves (or hacks away) the issue for now.

---

### Post by edscott on 2011-05-23
Oh, and just in case you really need to set the directory on which the dialog will open,
just do a plain chdir() before you create the dialog. The dialog will default to the current work directory.

---

