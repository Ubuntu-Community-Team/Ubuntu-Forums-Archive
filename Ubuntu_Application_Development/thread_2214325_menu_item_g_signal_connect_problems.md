---
title: "menu item g_signal_connect problems"
date: 2014-03-31
forum: Ubuntu Application Development
---

### Post by victwo on 2014-03-31
Hello.  I am new to the forum and have no idea why my g_signal_connects will not call my functions. 

g_signal_connect(paste, "activate", G_CALLBACK(paste_activated), NULL);

void paste_activated(GtkWidget *widget, gpointer user_data)
{
    printf("in paste_activated");
}//end paste_activated

Any ideas would be appreciated.  Thanks:P

Victor Twomey

---

