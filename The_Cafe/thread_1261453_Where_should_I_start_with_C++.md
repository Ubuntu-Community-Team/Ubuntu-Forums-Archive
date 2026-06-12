---
title: "Where should I start with C++?"
date: 2009-09-08
forum: The Cafe
---

### Post by dragos240 on 2009-09-08
I want to learn C++, I want to use it daily, I use java every once in a while, but i'm not that fluent in it. Where do I start?

---

### Post by NovaAesa on 2009-09-08
I would start with a simple hello world app. Should be rather easy. Also, it might be a good idea to start with a text editor and terminal window rather than relying on an IDE. That way you will understand what an IDE is actually doing when you hit compile.

A tip to beginners with C++: make sure you use g++ instead of gcc!

---

### Post by dragos240 on 2009-09-08
> **NovaAesa said:**
> I would start with a simple hello world app. Should be rather easy. Also, it might be a good idea to start with a text editor and terminal window rather than relying on an IDE. That way you will understand what an IDE is actually doing when you hit compile.

A tip to beginners with C++: make sure you use g++ instead of gcc!

Is g++ GNU++ :lolflag:?

---

### Post by Jimleko211 on 2009-09-08
I'm waiting for someone to post a good link for C++, as well, but as for text editors, my favorite is Kate.  I've tried Vim and Emacs, and I just don't like them, but I love Kate.  Kate allows me to set indentation and syntax highlighting, and even has a terminal so I can compile and execute my program from inside of it, without it hiding things from me.

Only downside is that it's a KDE app, but I don't really care about that.

---

### Post by dragos240 on 2009-09-08
> **Jimleko211 said:**
> I'm waiting for someone to post a good link for C++, as well, but as for text editors, my favorite is Kate.  I've tried Vim and Emacs, and I just don't like them, but I love Kate.  Kate allows me to set indentation and syntax highlighting, and even has a terminal so I can compile and execute my program from inside of it, without it hiding things from me.

Only downside is that it's a KDE app, but I don't really care about that.

Why is that a Downside?

---

### Post by Jimleko211 on 2009-09-08
Because some people get all iffy over the fact that KDE apps look different than GNOME apps and vice versa.

---

### Post by scragar on 2009-09-08
[http://www.freetechbooks.com/c-c-f3.html](http://www.freetechbooks.com/c-c-f3.html)

It's not the greatest resource in the world, but the books are, for the most part, very easy to pick up and easy to copy/paste from.

Oh, and they're real books for free in PDF format, so that's a + from me.

If you want to do anything graphical I say start learning qt, for more advanced graphics learn SDL, I'd keep away from GTK unless you have a good reason to prefer it.

---

### Post by phrostbyte on 2009-09-08
Here is a simple hello app in C++ to get you started

```

#include <iostream>
#include <string>
using namespace std;

int main()
{
   string name;

   cout << "What is your name? ";
   cin >> name;
   cout << "Hello " << name << "!" << endl;

   return 0;

}

```

Not sure if this will compile. :P

[This]("apt://build-essential") package is need for compiling.

The command to compile is (assuming that is file.cpp)

```
g++ file.cpp -o file
```

run with

```
./file
```

---

### Post by Jimleko211 on 2009-09-08
> **scragar said:**
> 

If you want to do anything graphical I say start learning qt, for more advanced graphics learn SDL, I'd keep away from GTK unless you have a good reason to prefer it.
Is the QT API better than GTK?

---

### Post by scragar on 2009-09-08
> **Jimleko211 said:**
> Is the QT API better than GTK?

I personally found it easier to pick up and use, and if you're beginning that's what you want.

Once you've played around with things for a while you can start using things that are harder to understand, but to begin with it's just easier to use QT than GTK.

---

### Post by forrestcupp on 2009-09-08
[Here's a good C++ tutorial.](http://www.cplusplus.com/doc/tutorial/)  I personally like wxWidgets for GUI stuff.  I'm sure a lot of people would argue with me about that one, though.

---

### Post by OutOfReach on 2009-09-08
> **Jimleko211 said:**
> Is the QT API better than GTK?

I find Qt's API better because it makes sense, and it's very easy to use, plus it has a large library for other things like networking, XML, etc

But I guess it's a matter of personal preference, look at both API's, etc and decide which one you like to work with.

---

### Post by Jimleko211 on 2009-09-08
Alright, then...I haven't looked at either API's, I always assumed I would just learn GTK 'cause most DE's and WM's use it.  When I get into graphical programming, though, I'll definitely look into it.  QT just got a lot more viable in my eyes.

---

### Post by Tamalin on 2009-09-08
Go to your local bookstore and buy a good book on C++, like 13.
"An Introduction to Object-Oriented Programming in C++ : With Applications in Computer Graphics", or "Core C++".  I have done this many times, and I always get good results from books (at least better than internet tutorials). However, I strongly hint that Java is more worth your while. :)

---

### Post by scragar on 2009-09-08
I would also like to suggest Thinking In C++ I should have mentioned this before, but I forgot it was sitting on my desktop. It's a really good source of code to play around with, since the code is tested to work not only with g++ but most other compilers and operating systems, giving you confidence that your code will work if you needed to compile it for something else.

---

### Post by ve4cib on 2009-09-08
I'll wade into the editor wars and suggest looking into Geany.  I've never used Kate, but I used to be a big fan of Gedit.  I tried out Geany on a whim a while back and have been using it exclusively at home (under Ubuntu with Gnome & Fluxbox) and at work (under Windows).  It's just great.  It's got the syntax highlighting and custom tools of Gedit, but it's also got code-folding, automatic symbol identification (you get a list of variables, constants, and functions that are automagically bookmarked for you), and it has a built-in terminal frame (no need to change windows when you want to recompile).

---

### Post by dragos240 on 2009-09-08
> **scragar said:**
> I personally found it easier to pick up and use, and if you're beginning that's what you want.

Once you've played around with things for a while you can start using things that are harder to understand, but to begin with it's just easier to use QT than GTK.

I like Gimp ToolKit. :) Also, what would be the issue in using GTK? How MUCH harder can it be?

---

### Post by scragar on 2009-09-08
> **dragos240 said:**
> I like Gimp ToolKit. :) Also, what would be the issue in using GTK? How MUCH harder can it be?

Code under here without libs, so it won't compile, but it does demonstrate the difficulty comparison.

GTK:```
## includes

static void hello( GtkWidget *widget, gpointer data ){
  g_print ("Hello World\n");
}

static gboolean delete_event( GtkWidget *widget, GdkEvent *event, gpointer data ){
  g_print ("delete event occurred\n");
  return TRUE;
}

static void destroy( GtkWidget *widget, gpointer data ){
  gtk_main_quit ();
}

int main( int argc, char *argv[] ){
  GtkWidget *window;
  GtkWidget *button;

  gtk_init (&argc, &argv);

  window = gtk_window_new (GTK_WINDOW_TOPLEVEL);

  g_signal_connect (G_OBJECT (window), "delete_event",
  G_CALLBACK (delete_event), NULL);

  g_signal_connect (G_OBJECT (window), "destroy",
  G_CALLBACK (destroy), NULL);

  gtk_container_set_border_width (GTK_CONTAINER (window), 10);

  button = gtk_button_new_with_label ("Hello World");

  g_signal_connect (G_OBJECT (button), "clicked",
  G_CALLBACK (hello), NULL);

  g_signal_connect_swapped (G_OBJECT (button), "clicked",
  G_CALLBACK (gtk_widget_destroy),
  G_OBJECT (window));

  gtk_container_add (GTK_CONTAINER (window), button);
  gtk_widget_show (button);
  gtk_widget_show (window);

  gtk_main ();

  return 0;
}
```

QT```

int main(int argc, char *argv[]){
  QApplication app(argc, argv);
  QPushButton hello("Hello world!");
  hello.resize(100, 30);
  hello.show();
  return app.exec();
}
```

---

### Post by dragos240 on 2009-09-08
Maybe I'll start with QT then :p

---

### Post by rkirk on 2009-09-08
From the looks of things, I might just have to give Qt a look... I use neither KDE nor GNOME, and I'm not exactly biased toward one over the other (though a lot of the apps I use happen to be GTK).

Though it's not as simple or as immediately satisfying right out of the gate, there's still something to be said for developing interfaces using the ncurses library.

---

### Post by Trail on 2009-09-09
Qt is good (even awesome; well structured, makes sense, powerful, etc), but it's NOT really C++. It's Qt/C++, in the sense that it adds a preprocessor stage in order to add some features like QObjects and signal/slot mechanisms and moc files and stuff like that.

If you do bother with C++, make sure you pay attention to the (std::*) standard library classes for things like strings, vectors, lists, etc ([http://www.cppreference.com/index.html](http://www.cppreference.com/index.html)). Keep in mind std::auto_ptr for when you are more fluent in C++.

---

### Post by Sporkman on 2009-09-09
> **Jimleko211 said:**
> Only downside is that it's a KDE app, but I don't really care about that.

It's also quite a resource hog for a mere fancy text editor.

---

### Post by Sporkman on 2009-09-09
BTW, feel free to mix C & C++. Many folks will gasp in shock and disapproval at this, but I frequently make use of both.

Contrary to popular belief, they are indeed the same language, and g++ will compile any mix of the two. In fact, I call the language C/C++.

---

### Post by Trail on 2009-09-09
> **Sporkman said:**
> BTW, feel free to mix C & C++. Many folks will gasp in shock and disapproval at this, but I frequently make use of both.

Contrary to popular belief, they are indeed the same language, and g++ will compile any mix of the two. In fact, I call the language C/C++.

Either you develop something as object oriented, or not. You can't really mix the paradigms. The syntax might be (almost) the same, but the way of thinking and the design patterns are very different. If you learn to express your code in OO, you'll probably be quite annoyed when someone claims that C is C++ (or that a language named C/C++ exists).

---

### Post by Sporkman on 2009-09-09
> **Trail said:**
> Either you develop something as object oriented, or not. You can't really mix the paradigms. The syntax might be (almost) the same, but the way of thinking and the design patterns are very different. If you learn to express your code in OO, you'll probably be quite annoyed when someone claims that C is C++ (or that a language named C/C++ exists).

I tend to use C++ OO + std libraries, and C I/O.

...so my stuff will have classes, std::vector/maps/lists, and use "new", but will also have printfs, sscanfs, FILE, etc.

---

### Post by GeneralZod on 2009-09-09
> **scragar said:**
> Code under here without libs, so it won't compile, but it does demonstrate the difficulty comparison.


I'm not sure if that's strictly fair, as that appears to be straight GTK rather than GTKMM, which is what someone writing C++ would use.

Having said that: Qt simply rocks my world, even when I'm using e.g. ruby instead of C++ :)

---

### Post by keiichidono on 2009-09-09
> **GeneralZod said:**
> I'm not sure if that's strictly fair, as that appears to be straight GTK rather than GTKMM, which is what someone writing C++ would use.

Having said that: Qt simply rocks my world, even when I'm using e.g. ruby instead of C++ :)

Even then it's not much better.
[PHP]//HelloWorldWindow.h
#ifndef HELLOWORLDWINDOW_H__
#define HELLOWORLDWINDOW_H__
 
#include <gtkmm/window.h>
#include <gtkmm/button.h>
 
// Derive a new window widget from an existing one.
// This window will only contain a button labelled "Hello World"
class HelloWorldWindow : public Gtk::Window
{
  public:
    HelloWorldWindow( );
    ~HelloWorldWindow( );
 
  protected:
    void on_button_clicked( ); //event handler
 
    Gtk::Button hello_world;
};
 
#endif
//HelloWorldWindow.cc
#include <iostream>
#include "HelloWorldWindow.h"
 
HelloWorldWindow::HelloWorldWindow( )
 : hello_world( "Hello World" )
{
    // Set the title of the window.
    set_title( "Hello World" );
 
    // Add the member button to the window,
    add( hello_world );
 
    // Handle the 'click' event.
    hello_world.signal_clicked( ).connect(
        sigc::mem_fun( *this, &HelloWorldWindow::on_button_clicked ) );
 
    // Display all the child widgets of the window.
    show_all_children( );
}
 
void HelloWorldWindow::on_button_clicked( )
{
    std::cout << "Hello world" << std::endl;
}
 
HelloWorldWindow::~HelloWorldWindow()
{
}
//main.cc
#include <gtkmm/main.h>
#include "HelloWorldWindow.h"
 
int main( int argc, char *argv[] )
{
    // Initialization
    Gtk::Main kit( argc, argv );
 
    // Create a hello world window object
    HelloWorldWindow example;
 
    // gtkmm main loop
    Gtk::Main::run( example );
    return 0;
}[/PHP]
But with PyGTK you have.
[PHP]import gtk
 
def createWindow():
    window = gtk.Window()
    window.set_default_size(200, 200)
    window.connect('destroy', gtk.main_quit)
 
    label = gtk.Label('Hello World')
    window.add(label)
 
    label.show()
    window.show()
 
createWindow()
gtk.main()[/PHP]
That said i use gtk and love it for python but for c/cpp i use qt.

---

### Post by ve4cib on 2009-09-09
> **Trail said:**
> Either you develop something as object oriented, or not. You can't really mix the paradigms. The syntax might be (almost) the same, but the way of thinking and the design patterns are very different.

I also tend to write in a hybrid C/C++ way.  I'll use OO approaches for places where it makes sense (complex data data structures for example), but I tend to use C-style procedural approaches for mainline functions (main itself, and functions that are only ever called from/used by main -- command-line argument parsing is a good example of that).  Random utility functions will also often get the C-treatment since they're used all over the place and I don't want to have to reference a Util class every time I need to use them.

I also tend to prefer C's way of dealing with IO.  I've just gotten used to using printf, FILE*, etc...  And for basic IO I've yet to see any really convincing reason to avoid these.  If you're doing something particularly complex that C++'s cin and cout does, then go for it.  But when I just want to print "Insufficient arguments" I'll just stick with cstdio.


From a hardcore optimization perspective  historically-speaking object-oriented solutions tended to be slightly slower than their procedural counterparts.  More memory-access/pointer de-referencing or something like from what I vaguely recall of my programming language concepts course back in third-year.  It meant that if speed of execution was absolutely-critical then OO was a bad approach.  But you can't deny OO's ability to handle complex data structures and inheritance much more cleanly.  So hybrid approaches were fairly common for a long time; use OO where you need to represent complex data, but use non-OO for everything else.

Of course these days computers are fast enough and compilers good enough at optimizing that this reasoning for hybrid-coding is largely obsolete.  But there are enough old pieces of code floating around that it's not uncommon to come across examples of this in practice.


Ultimately though as long as your code works and is **well-documented*** that's what really matters.  Adherence to one particular paradigm or another is secondary in my opinion.


**many programmers sadly neglect that part of coding, much to the annoyance of everyone who has to look at it later*

---

