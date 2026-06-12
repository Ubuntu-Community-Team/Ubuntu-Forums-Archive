---
title: "PyGobject Callback Signature"
date: 2013-11-20
forum: Ubuntu Application Development
---

### Post by Anonimista on 2013-11-20
(I wasn't sure if I should post this here or in the 'Absolute Beginners' Section', but it's a development question, so I'll post it here.)

I found several tutorials, like [The Python GTK+ 3 Tutorial]("http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html"), which is pretty nice for a novice.

I am struggling to find PyGObject documentation, I am not clear on the callback functions signature. In the above tutorial the connect() call looks like this

```
self.button.connect("clicked", self.on_button_clicked)
```

and the callback looks like this:

```
def on_button_clicked(self, widget):
          print("Hello World")
```

the widget parameter being the button which connect() was called (am I right?). Elsewhere I have seen callbacks like this:

```
def on_button_clicked(self, widget, data=None):
          print("Hello World")
```

On [gnome.org]("https://developer.gnome.org/gobject/stable/gobject-Closures.html#GCallback") I fount this:

' The required signature of a callback function is determined by the context in which is used (e.g. the signal to which it is connected).'

I would like to know how could I determine the appropriate callback signature for any given signal. Thanks in advance.

---

### Post by Anonimista on 2013-11-25
To answer the question, I should have read the documentation. For example [GtkButton clicked signal]("https://developer.gnome.org/gtk3/3.2/GtkButton.html#GtkButton-clicked").

---

