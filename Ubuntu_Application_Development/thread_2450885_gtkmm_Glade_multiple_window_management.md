---
title: "gtkmm Glade multiple window management"
date: 2020-09-22
forum: Ubuntu Application Development
---

### Post by anshah on 2020-09-22
I am using gtkmm and Glade on Ubuntu 14.04 Gnome desktop and I am using the GNOME example file to load a Glade UI file:

I'm just getting started with gtkmm and Glade in C++. I was going through the tutorial and was able to create and load a Glade UI XML file with the provided code:


```
#include <gtkmm.h>
#include <iostream>


Gtk::Dialog* pDialog = nullptr;


static
void on_button_clicked()
{
  if(pDialog)
    pDialog->hide(); //hide() will cause main::run() to end.
}


int main (int argc, char **argv)
{
  auto app = Gtk::Application::create(argc, argv, "org.gtkmm.example");


  //Load the GtkBuilder file and instantiate its widgets:
  auto refBuilder = Gtk::Builder::create();
  try
  {
    refBuilder->add_from_file("basic.glade");
  }
  catch(const Glib::FileError& ex)
  {
    std::cerr << "FileError: " << ex.what() << std::endl;
    return 1;
  }
  catch(const Glib::MarkupError& ex)
  {
    std::cerr << "MarkupError: " << ex.what() << std::endl;
    return 1;
  }
  catch(const Gtk::BuilderError& ex)
  {
    std::cerr << "BuilderError: " << ex.what() << std::endl;
    return 1;
  }


  //Get the GtkBuilder-instantiated Dialog:
  refBuilder->get_widget("DialogBasic", pDialog);
  if(pDialog)
  {
    //Get the GtkBuilder-instantiated Button, and connect a signal handler:
    Gtk::Button* pButton = nullptr;
    refBuilder->get_widget("quit_button", pButton);
    if(pButton)
    {
      pButton->signal_clicked().connect( sigc::ptr_fun(on_button_clicked) );
    }


    app->run(*pDialog);
  }


  delete pDialog;


  return 0;
}

```

My project will eventually be multiple windows that contain different widgets. I plan to have multiple windows in my project for example:


 - basic1.glade
 - basic2.glade
 - basic3.glade


I need to switch to corresponding glade windows based on my UI state. I have searched all over and have not seen any examples how gtkmm can transition to another glade ui file.
Basically my question is how does multiple window management work in gtkmm with multiple glade ui XML files?

---

