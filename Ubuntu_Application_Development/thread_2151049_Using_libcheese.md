---
title: "Using libcheese"
date: 2013-06-03
forum: Ubuntu Application Development
---

### Post by seleoCF on 2013-06-03
Hi all,

I am learning how to write applications for linux using gtkmm. My goal is write an application that uses webcam to do some stuffs. Since my Ubuntu is gnome based, I am trying to use the libcheese library and related software in an application I have written using ecplise + glade designer + gtkmm. My problem is that I cannot find a good explanation on how libcheese work. I need an example on how to inizialize it. My idea is to add a cheese-widget in my gui.glade file or by code but cannot figure how to do it. There is someone experienced with it that can help me?

---

### Post by MG&amp;TL on 2013-06-03
> **seleoCF said:**
> Hi all,

I am learning how to write applications for linux using gtkmm. My goal is write an application that uses webcam to do some stuffs. Since my Ubuntu is gnome based, I am trying to use the libcheese library and related software in an application I have written using ecplise + glade designer + gtkmm. My problem is that I cannot find a good explanation on how libcheese work. I need an example on how to inizialize it. My idea is to add a cheese-widget in my gui.glade file or by code but cannot figure how to do it. There is someone experienced with it that can help me?

I don't know if you've seen this page? [https://developer.gnome.org/cheese/3.6/](https://developer.gnome.org/cheese/3.6/) ? It's the API reference for cheese. There is a section on initialisation.

---

### Post by seleoCF on 2013-06-03
Yes I already know the reference, but it is very minimal. It does not explain anything, I think I need some example on how to add a cheese-widget on my gui.

---

### Post by seleoCF on 2013-06-03
My code:

```


//------------------------------------------------------------------------------
#include <iostream>
#include <gtkmm.h>
#include "FrmMain.h"
#include <cheese/cheese.h>
#include <cheese/cheese-camera.h>
#include <cheese/cheese-camera-device.h>
#include <cheese/cheese-camera-device-monitor.h>
#include <cheese/cheese-widget.h>
#include <cheese/cheese-gtk.h>
//------------------------------------------------------------------------------
#define IMAGE_FILE    "image.png"
//------------------------------------------------------------------------------
using namespace std;
using namespace Gtk;
//------------------------------------------------------------------------------
bool OnDrwAreaDrawSignal(const Cairo::RefPtr<Cairo::Context> &ccontext,Gtk::DrawingArea *drawarea);
//------------------------------------------------------------------------------
int main (int argc, char *argv[])
{
    int a = 0;
    char ***b = NULL;

    cout << "Avvio applicazione" << endl;

    // Creiamo un oggetto di tipo Gtk::Main. Il costruttore di questo oggetto
    // inizializza una sessione gtkmm e controlla gli argomenti passati al
    // programma. Questa operazione è necessaria in ogni applicazione gtkmm.
    Gtk::Main kit(argc, argv);

    // Leggiamo il file xml
    Glib::RefPtr<Gtk::Builder> builder = Gtk::Builder::create_from_file("gui.glade");

    // Creiamo un puntatore a finestra
    FrmMain *frm = 0;

    // Associamo la finestra a quella descritta dal file
    builder->get_widget_derived("frmMain", frm);

    // Carichiamo una immagine per lo sfondo
    try {
        frm->BGImage = Gdk::Pixbuf::create_from_file(IMAGE_FILE);
    }
    catch(const Glib::FileError& errore) {
        cerr << "Errore File: " << errore.what() << endl;
    }
    catch(const Gdk::PixbufError& errore) {
        cerr << "Errore PixBuf: " << errore.what() << endl;
    }

    // Inizializzazione libcheese
//    cout << "Inizializzazione libcheese ..." << endl;
//    if( !cheese_init(a,b) ) {
//        cerr << "cheese_init() fallita" << endl;
//        return -1;
//    }
    if( !cheese_gtk_init(&a,b) ){
        cerr << "cheese_gtk_init() fallita" << endl;
        return -1;
    }
    cout << "Fine inizializzazione libcheese" << endl;

    // Avviamo il loop delle gtk
    kit.run(*frm);

    cout << "Termine applicazione" << endl;

    return 0;
}


```


gives a  segmentation error. Why?

---

### Post by MG&amp;TL on 2013-06-03
> **seleoCF said:**
> 
gives a  segmentation error. Why?

Sorry I can't be more help; I've never actually used cheese, just wondered if you'd found the API reference or not.

Which line does the program crash on? You should use a debugger like *gdb* if you don't know.

---

### Post by seleoCF on 2013-06-04
it is cheese_gtk_init(&a,b) that makes the error

---

### Post by MG&amp;TL on 2013-06-04
> **seleoCF said:**
> it is cheese_gtk_init(&a,b) that makes the error

Okay, I just read your code a bit more closely. Why are you giving it 0 and NULL as arguments? It expects the contents of *argc *and *argv*. Try:

```
cheese_gtk_init(&argc, &argv)
```

---

### Post by seleoCF on 2013-06-07
I just made a try. In fact, originally, I have written code as you suggested to me but it makes the same segmentation error. I started thinking that some thing is missing before initializing the cheese gtk lib

---

### Post by MG&amp;TL on 2013-06-07
> **seleoCF said:**
> I just made a try. In fact, originally, I have written code as you suggested to me but it makes the same segmentation error. I started thinking that some thing is missing before initializing the cheese gtk lib

Mmm. Have you tried asking on an IRC channel? There's usually at least one person who's been there and done that.
Just as a check, do any of the cheese-based applications work (try *cheese*) - it might be that *cheese* itself is broken on your hardware?

---

### Post by seleoCF on 2013-06-07
I have placed the cheese_gtk_init BEFORE Gtk::Main kit(); and it do not longer gives me the segmentation error

---

