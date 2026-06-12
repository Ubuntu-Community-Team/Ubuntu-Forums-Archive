---
title: "QT is better than GTK+"
date: 2009-09-19
forum: The Cafe
---

### Post by keiichidono on 2009-09-19
The evidence:

GTK+ hello world:
[PHP] #include <gtk/gtk.h>
 
 int main (int argc, char *argv[])
 {
    GtkWidget *window;
    GtkWidget *label;
 
    gtk_init (&argc, &argv);
 
    /* create the main, top level, window */
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
 
    /* give it the title */
    gtk_window_set_title (GTK_WINDOW (window), "Hello World");
 
    /* Connect the destroy signal of the window to gtk_main_quit
     * When the window is about to be destroyed we get a notification and
     * stop the main GTK+ loop
     */
    g_signal_connect (window, "destroy",
                      G_CALLBACK (gtk_main_quit), NULL);
 
    /* Create the "Hello, World" label  */
    label = gtk_label_new ("Hello, World");
 
    /* and insert it into the main window  */
    gtk_container_add (GTK_CONTAINER (window), label);
 
    /* make sure that everything, window and label, are visible */
    gtk_widget_show_all (window);
 
    /* start the main loop, and let it rest there until the application is closed */
    gtk_main ();
 
    return 0;
 }[/PHP]

and a Qt hello world:
[PHP]#include <QtGui>
 
int main(int argc, char *argv[])
{
    QApplication app(argc, argv);
    QLabel label("Hello, world!");
    label.show();
    return app.exec();
}[/PHP]

Whiners:* But gtk+ is in c and qt is in cpp it's not a fair comparison*

Well, it gets even worse with gtkmm:
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

Whiners: *But the THEMES are better in gtk+!*

[QUOTE=Wikipedia]....Despite the incomplete state of Metacity theme development documentation, many themes have been written for Metacity. A huge number of such themes can be downloaded from GNOME's art site, art.gnome.org....[/QUOTE]

Suckers: *ALL HOPE IS GONE! WE MUST SWITCH TO QT!!!*

[IMG]http://img190.imageshack.us/img190/3673/whoawhoatakeashowah.png[/IMG]

There is hope in GTK+3, our beloved toolkit is saved.

[QUOTE=Wikipedia]Project Ridley is an attempt to consolidate several libraries that are currently external to GTK+, including libgnome, libgnomeui, libgnomeprint22, libgnomeprintui22, libglade, libgnomecanvas, libegg, libeel, gtkglext and libsexy.
Developers are also considering new directions for the library, including breaking ABI, removing deprecated API components, and adding an integrated scene graph system, similar to the Clutter graphics library, effectively integrating GTK+ with OpenGL.
Development and design of the GTK+ 3 release of the toolkit started in February 2009 during the GTK+ Theming Hackfest held in Dublin. A first draft of the development roadmap has been released on April 9th, 2009.[/QUOTE]

Anyone wanna prove me wrong or have any thoughts? :P

---

### Post by scragar on 2009-09-19
[I posted about this before ya. I win. :p](http://ubuntuforums.org/showpost.php?p=7919539&postcount=18)

---

### Post by keiichidono on 2009-09-19
Yeah but i have a meme. :lolflag:

---

### Post by Exodist on 2009-09-19
Yea I am keeping my fingers crossed also for GTK3. 
Not to mention it will help take the hell out of compiling gnomey from scratch since their reworking and consolidating many deps and removing old ones deps not used anymore..

---

### Post by fela on 2009-09-19
I much prefer QT4 to GTK2, but I prefer GTK2 to QT3 mainly because QT3 isn't under the GPL. Or is it.

---

### Post by dernob on 2009-09-19
Qt3 was GPL. But not LGPL (instead of GTK). Qt (>=4.5) is LGPL.

---

### Post by fela on 2009-09-19
> **dernob said:**
> Qt3 was GPL. But not LGPL (instead of GTK). Qt (>=4.5) is LGPL.

Right. I don't feel guilty about using amarok 1.4 anymore :)

---

### Post by mmix on 2009-09-19
Slightly offtopic, but i would bet haiku's GUI is better than gtk+/qt/xorg.

---

### Post by dragos240 on 2009-09-19
Just because it's harder, doesn't mean it's better.

---

### Post by Tibuda on 2009-09-19
[http://ubuntuforums.org/showpost.php?p=6558543&postcount=72](http://ubuntuforums.org/showpost.php?p=6558543&postcount=72)

And that Gtkmm code is unfair too. It does more than the Qt hello world, uses proper object orientation and a separate header file. You can rewrite all that to a single main function. Manage a big project in one function.

---

### Post by Pasdar on 2009-09-19
> **dragos240 said:**
> Just because it's harder, doesn't mean it's better.

It's not about the code being harder or easier to write. It's about the amount of code the machine has to go through to get to the same result. E.g.: having to go through 200 lines of code just to write, "Hello World", instead of just 5 lines of code.

---

### Post by Namtabmai on 2009-09-19
Hello, World isn't the best example you can use, in fact it's one of the worst.

I haven't written a Hello World application since the first year of university. All I think when I see a Hello World example written in 5 lines is, "How difficult is it going to be to get it to do something more complex?".

Just because a library allows you to write easy programs easily doesn't necessarily mean it's going to allow you to write complex programs with easy. In fact from my experience it's quite the opposite.

---

### Post by geoken on 2009-09-19
> **Pasdar said:**
> It's not about the code being harder or easier to write. It's about the amount of code the machine has to go through to get to the same result. E.g.: having to go through 200 lines of code just to write, "Hello World", instead of just 5 lines of code.

Frequently the 200 line file will be faster to execute. The code doesn't get reduced 40 fold magically, there is a bunch of extra interpretation going on behind the scenes.

---

### Post by geoken on 2009-09-19
> **Namtabmai said:**
> Hello, World isn't the best example you can use, in fact it's one of the worst.


Agreed. All a hello world example does is illustrate the difference between a basic application setup code. So one language may auto import a bunch of stuff and the main class may automatically add a certain display objects where the other language may be more flexible and allow you to create a lighter application without forcing in a bunch of libs.

---

### Post by tcoffeep on 2009-09-19
gtk+ > qt

---

### Post by Murrquan on 2009-09-19
I like GTK+ because it works with the Global Menu Applet. ^.^

I just hope it's easy to develop for, because I'm planning on learning C# ...

---

### Post by SunnyRabbiera on 2009-09-19
Besides if QT was superior then how come KDE4 is so limited?

---

### Post by Colonel Kilkenny on 2009-09-19
> **SunnyRabbiera said:**
> Besides if QT was superior then how come KDE4 is so limited?

If I'm eating apples why are the oranges orange. Qt is Qt, KDE4 is KDE4. GTK+ ain't Gnome, Qt ain't KDE.

PS. Qt is superior :)

---

### Post by CJ Master on 2009-09-19
> **tcoffeep said:**
> gtk+ > qt

Your sources and reasons truly overwhelm me. :roll:

---

### Post by kevCast on 2009-09-19
I think you guys are missing the attractions of GTK. I love QT4 and all it's features, which GTK2 cannot really compete with. However, GTK doesn't really change, and it's a safe bet to write applications in. QT3 to QT4 broke a lot of applications, the majority of them having to be rewritten. Amarok, K3B, Koffice, etc. can be examples of this.

GTK2 to GTK3 however won't break anything aside from legacy software. The majority of applications will just have to recompiled against GTK3. So, yes, while it may take less lines of code to write the QT application, people who are switching from QT3 feel like they have to write their program twice.

---

### Post by hoppipolla on 2009-09-19
My vote goes for Qt but I think I've had this argument too many times to get stuck in again hehe ^_^

---

### Post by chucky chuckaluck on 2009-09-19
> **SunnyRabbiera said:**
> Besides if QT was superior then how come KDE4 is so limited?

that's like saying "if wheat flour is so superior, then how come your brother sucks at baking?"

---

### Post by hoppipolla on 2009-09-19
> **chucky chuckaluck said:**
> that's like saying "if wheat flour is so superior, then how come your brother sucks at baking?"

Haha well said :)

And personally I think KDE 4 feels a bit limited at the moment as it still has a bit of development to go before it's as mature as Gnome 2 :)

---

### Post by tcoffeep on 2009-09-19
> **CJ Master said:**
> Your sources and reasons truly overwhelm me. :roll:

I don't need sources or reasons. I'm stating a personal opinion. I do not use QT apps at all on my computer, and use only GTK+ apps.

---

### Post by kevCast on 2009-09-19
> **hoppipolla said:**
> Haha well said :)

And personally I think KDE 4 feels a bit limited at the moment as it still has a bit of development to go before it's as mature as Gnome 2 :)

And they're both lacking compared to Xfce, IMO.

---

### Post by Starlight on 2009-09-19
I wish just one toolkit became a standard for Linux apps and desktop environments... I don't really care which one, it could be GTK+, Qt, or something else, as long as all or almost all apps would use it, and it had many nice looking themes with animations and transparency effects.

---

### Post by hoppipolla on 2009-09-19
> **Starlight said:**
> I wish just one toolkit became a standard for Linux apps and desktop environments... I don't really care which one, it could be GTK+, Qt, or something else, as long as all or almost all apps would use it, and it had many nice looking themes with animations and transparency effects.

Personally, PERSONALLY, I think it will. Very soon. And I think that it will be Qt :)

---

### Post by CJ Master on 2009-09-19
> **tcoffeep said:**
> I don't need sources or reasons. I'm stating a personal opinion. I do not use QT apps at all on my computer, and use only GTK+ apps.

GTK sucks. There, I stated my personal opinion with no reasons behind it. The world is better for that, right?

---

### Post by Exodist on 2009-09-19
> **hoppipolla said:**
> Personally, PERSONALLY, I think it will. Very soon. And I think that it will be Qt :)

Nah.. Python  :popcorn:

---

### Post by earthpigg on 2009-09-19
> **Starlight said:**
> I wish just one toolkit became a standard for Linux apps and desktop environments... I don't really care which one, it could be GTK+, Qt, or something else, as long as all or almost all apps would use it, and it had many nice looking themes with animations and transparency effects.

done. it's gtk.

---

### Post by RiceMonster on 2009-09-19
> **SunnyRabbiera said:**
> Besides if QT was superior then how come KDE4 is so limited?

[img]http://www.meikathon.net/roflmao/facepalm.jpg[/img]

---

### Post by hoppipolla on 2009-09-19
> **CJ Master said:**
> GTK sucks. There, I stated my personal opinion with no reasons behind it. The world is better for that, right?

Now now CJ... lol :)

Although you do have a point lol

---

### Post by hoppipolla on 2009-09-19
I say let's make QTK ^_^

---

### Post by larky on 2009-09-19
I have been with gtk for over 5 years and love it, and don't plan on switching. Now I will 

say QT is better.:popcorn: but it's no big deal.

---

### Post by Starlight on 2009-09-19
> **hoppipolla said:**
> Personally, PERSONALLY, I think it will. Very soon. And I think that it will be Qt :)
That's possible, since KDE 4 is getting better and better, and it's using Qt. so maybe Qt will become more popular. I've read somewhere recently that the next KDE 4.4 will use a new version of Qt that includes some new animation framework... it sounds good, maybe it would mean that the Oxygen Qt theme will have cool effects like the ones Plasma has :)

> **earthpigg said:**
> done. it's gtk.

GTK is good, but Qt seems to have more features when it comes to themes. It doesn't have as many themes as GTK, but Bespin has some extremely cool stuff that no GTK theme has :D But maybe GTK+ 3 will also have some interesting things. :)

---

### Post by days_of_ruin on 2009-09-19
Gtk has many more language bindings because:

1. It is written in c, which makes it a lot easier to write bind
ings for it.
 
2. Gobject introspection. Does Qt have Javascript bindings?

And for all you people wishing for only one toolkit, Qt has 3, yes 3 different python bindings.

Does Qt have anything like Clutter?

This is fine if you like the default window size.
And default window title, and no callbacks. The Gtk hello world teaches you a lot more about gtk than this teaches you about Qt.

```
int main(int argc, char *argv[]) 
{ 
    QApplication app(argc, argv); 
    QLabel label("Hello, world!"); 
    label.show(); 
    return app.exec(); 
}  
```

---

### Post by hoppipolla on 2009-09-19
> **Starlight said:**
> GTK is good, but Qt seems to have more features when it comes to themes. It doesn't have as many themes as GTK, but Bespin has some extremely cool stuff that no GTK theme has :D But maybe GTK+ 3 will also have some interesting things. :)

My eyes are peeled for GTK3 :)

But yeah I do feel though that KDE 4 as a flagship for Qt will continue to get better at an amazing pace :)

---

### Post by earthpigg on 2009-09-19
the knowledgeable can discuss whether or not black holes exist on the merits of the science and theory.

the ignorant, like me, need to rely on people better informed.

i do not know how to program.

here is what i do know....

Desktop Environments using Qt:
[LIST]
[*]KDE
[/LIST]

Desktop Enviornments using GTK+:
[LIST]
[*]GNOME
[*]xfce
[*]lxde (which i use)
[*]maemo (if i where to get a smartphone today, it would be one of these)
[*]OLPC
[/LIST]

(did i leave any DE's out of the Qt list?)

though i do not know how to program, i do know that everyone but that goofy Kousin Karl seems to us GTK+ for desktop environments... especially for young projects, that have the advantages of learning from mistakes of the past.

---

### Post by hoppipolla on 2009-09-19
> **earthpigg said:**
> the knowledgeable can discuss whether or not black holes exist on the merits of the science and theory.

the ignorant, like me, need to rely on people better informed.

i do not know how to program.

here is what i do know....

Desktop Environments using QT:
KDE 

Desktop Enviornments using GTK+:
GNOME
xfce
lxde (which i use)
maemo (if i where to get a smartphone today, it would be one of these)
OLPC



though i do not know how to program, i do know that everyone but that goofy Kousin Karl seems to us GTK+ for desktop environments...

Yeah but look what goofy Kousin Karl has done with it! ^_^

---

### Post by -grubby on 2009-09-19
Generally speaking, I have to agree with the OP, QT does seems nicer to program in than GTK. The differences are less so in my language of choice (Python), but still noticable.

[quote=kevCast]
QT3 to QT4 broke a lot of applications, the majority of them having to be rewritten.
[/quote]

You don't have to rewrite your applications when your toolkit has a new version.

---

### Post by chucky chuckaluck on 2009-09-19
> **earthpigg said:**
> the knowledgeable can discuss whether or not black holes exist on the merits of the science and theory.

the ignorant, like me, need to rely on people better informed.

i do not know how to program.

here is what i do know....

Desktop Environments using Qt:
[LIST]
[*]KDE
[/LIST]

Desktop Enviornments using GTK+:
[LIST]
[*]GNOME
[*]xfce
[*]lxde (which i use)
[*]maemo (if i where to get a smartphone today, it would be one of these)
[*]OLPC
[/LIST]

(did i leave any DE's out of the Qt list?)

though i do not know how to program, i do know that everyone but that goofy Kousin Karl seems to us GTK+ for desktop environments... especially for young projects, that have the advantages of learning from mistakes of the past.

so, 'most popular' = best?

---

### Post by earthpigg on 2009-09-19
this is interesting:

[http://en.wikipedia.org/wiki/Qt_%28toolkit%29](http://en.wikipedia.org/wiki/Qt_%28toolkit%29)

> It is produced by ***Nokia's*** Qt Development Frameworks division

[http://en.wikipedia.org/wiki/Maemo](http://en.wikipedia.org/wiki/Maemo)

> Maemo, spelled "MyMo(bile)", originally named "Internet Tablet OS"[citation needed], is a software platform developed by ***Nokia*** for their line of Internet Tablets.

...

It uses the Matchbox window manager, and the ***GTK-based*** Hildon as its GUI and application framework.


even the company that ***develops*** Qt chooses GTK+ over Qt!!



again, i want to emphasize that i am fully aware of my ignorance. i can no more prove through objective reasoning that GTK+ is better than i can prove through objective reasoning that black holes exist.


but a whole bunch of people a lot better informed than me seem to prefer to believe that black holes exist, and that GTK+ is superior.

---

### Post by kevCast on 2009-09-19
> **-grubby said:**
> Generally speaking, I have to agree with the OP, QT does seems nicer to program in than GTK. The differences are less so in my language of choice (Python), but still noticable.



You don't have to rewrite your applications when your toolkit has a new version.

You don't have to, but I was under the impression that QT3 application developers had to to take advantage of QT4.

---

### Post by hoppipolla on 2009-09-19
[http://www.youtube.com/watch?v=dOI0DmGppLw](http://www.youtube.com/watch?v=dOI0DmGppLw) (results speak for themselves :) )

---

### Post by GeneralZod on 2009-09-19
> **earthpigg said:**
> 
even the company that ***develops*** Qt chooses GTK+ over Qt!!

Nokia used GTK *before* they bought TrollTech.  In fact, their expressed dissatisfaction with GTK was almost certainly one of the primary reasons for the TrollTech purchase.

Future versions of Maemo will be based on Qt, as revealed at this year's Guademy.

---

### Post by Namtabmai on 2009-09-19
> **earthpigg said:**
> i do know that everyone but that goofy Kousin Karl seems to us GTK+

I'd like to think that as Linux users we'd all appreciate that popularity/usage doesn't necessarily tie in with quality.

Let's also remember it was only in 2005 that Qt changed it's license, before then free cross platform application couldn't use Qt on Windows due to the propriety license.

A large majority of Linux applications are cross platform and if you're writing one you'd be crazy to have choosen a GUI toolkit that prohibits you from porting it to Windows.

---

### Post by earthpigg on 2009-09-19
> **chucky chuckaluck said:**
> so, 'most popular' = best?

that logic would indeed be horribly flawed if programmers where ignorant masses that go with the flow and incapable of independent decision making.

are they?

GTK+ is the 'most popular' amongst well informed people that have *produced* tangible products. the proof is in the pudding. krazy kousin karl is great, but all he has is KDE.

believing in black holes is the 'most popular' amongst well informed scientists. fundamentalist Christians are great, but all they have is "the earth was created 6000 years ago..."



and let's consider where GTK+ has no reason to be popular: at Nokia, where Qt is developed. Nokia, who chose GTK+ over Qt for the maemo.

---

### Post by earthpigg on 2009-09-19
> Future versions of Maemo will be based on Qt, as revealed at this year's Guademy.

fair enough.

glad i put the 'i know i dont know wtf i am talking about' disclaimer in my first post.

sometimes, the quickest way to learn is to stir up the pot.

---

### Post by qazwsx on 2009-09-19
> **earthpigg said:**
> 
Desktop Enviornments using GTK+:
[...]
[*]maemo (if i where to get a smartphone today, it would be one of these)

I think it is currently QT. It was shamefully gtk+ for a while.

---

### Post by phrostbyte on 2009-09-19
My opinion..

The advantage GTK+ has over Qt is it implements the GObject object model, which makes writing language bindings for GTK+ really easy (and mostly automatic). It also made possible languages like Vala, which is basically syntactic sugar over GObject.

Qt has a much cleaner (core) API though, and significantly more functionality as a widget toolkit, as well as better cross-platform support. C++ is better suited to implement a widget toolkit because it's very easy to consider a widget as a object. Actually the popular of C++ can be shown to be around the same time GUI became mainstream. But arguably GObject has a much more robust object model then C++, it's just a pain to work with from C.

---

### Post by GeneralZod on 2009-09-19
As for the bindings thing: Writing bindings to C++ "from scratch" is certainly harder than to C (although neither can really be called "easy"), but KDE have the "smoke" library which hugely simplifies this and makes keeping them up to date almost completely automatic.  Going the other way, there is also Kross which allows scripting languages (with a Kross backend) to be seamless embedded into KDE apps.  You don't even have to write bindings for the scripting API you expose: signals and slots can be inspected (and invoked) at runtime.

An earlier poster asked if Qt had Javascript bindings: the answer is yes (Amarok uses them for its scripting support), although they are currently being re-written to use Smoke instead of Qt's generator.

---

### Post by hoppipolla on 2009-09-19
> **GeneralZod said:**
> As for the bindings thing: Writing bindings to C++ "from scratch" is certainly harder than to C (although neither can really be called "easy"), but KDE have the "smoke" library which hugely simplifies this and makes keeping them up to date almost completely automatic.  Going the other way, there is also Kross which allows scripting languages (with a Kross backend) to be seamless embedded into KDE apps.  You don't even have to write bindings for the scripting API you expose: signals and slots can be inspected (and invoked) at runtime.

An earlier poster asked if Qt had Javascript bindings: the answer is yes (Amarok uses them for its scripting support), although they are currently being re-written to use Smoke instead of Qt's generator.

It's really cool to hear someone who actually knows Qt quite well talk about it!

I go on about KDE and Qt and how great I think it is all the time, but I'm basically just a fanboy lol :)

Who knows maybe I'll learn to code someday in the future ^_^

---

### Post by Paqman on 2009-09-19
> **hoppipolla said:**
> Personally, PERSONALLY, I think it will. Very soon. And I think that it will be Qt :)

I think it'll probably happen about the same time we all decide to standardise on rpm/deb. Translation: never. Standardising Linux is like herding cats.

---

### Post by Skripka on 2009-09-19
> **Paqman said:**
> I think it'll probably happen about the same time we all decide to standardise on rpm/deb. Translation: never. Standardising Linux is like herding cats.

Standardising Linux is harder.  Herding cats is as easy as popping open a can of tuna.

---

### Post by chucky chuckaluck on 2009-09-19
> **earthpigg said:**
> that logic would indeed be horribly flawed if programmers where ignorant masses that go with the flow and incapable of independent decision making.

are they?

GTK+ is the 'most popular' amongst well informed people that have *produced* tangible products. the proof is in the pudding. krazy kousin karl is great, but all he has is KDE.

believing in black holes is the 'most popular' amongst well informed scientists. fundamentalist Christians are great, but all they have is "the earth was created 6000 years ago..."

and let's consider where GTK+ has no reason to be popular: at Nokia, where Qt is developed. Nokia, who chose GTK+ over Qt for the maemo.

> **earthpigg said:**
> glad i put the 'i know i dont know wtf i am talking about' disclaimer in my first post.

me too. 

unless you understand why a majority might choose something, saying it's *better* because the majority prefer it, is not a particularly persuasive argument. the history of qt's 'free'-ness, at least, taints the argument in this case.

---

### Post by days_of_ruin on 2009-09-19
> **hoppipolla said:**
> It's really cool to hear someone who actually knows Qt quite well talk about it!

I go on about KDE and Qt and how great I think it is all the time, but I'm basically just a fanboy lol :)

Who knows maybe I'll learn to code someday in the future ^_^

Non-programmer who is a Qt fanboy?

---

### Post by earthpigg on 2009-09-19
> **chucky chuckaluck said:**
> me too. 

unless you understand why a majority might choose something, saying it's *better* because the majority prefer it, is not a particularly persuasive argument. the history of qt's 'free'-ness, at least, taints the argument in this case.

the 'free'-ness issue was sort of what i was looking for:

"if Qt is better, why do so many devs pick GTK+?"

the Free thing answered it.

---

### Post by hoppipolla on 2009-09-19
> **chucky chuckaluck said:**
> me too. 

unless you understand why a majority might choose something, saying it's *better* because the majority prefer it, is not a particularly persuasive argument. the history of qt's 'free'-ness, at least, taints the argument in this case.

So when did it become totally "free"? ^_^

I wonder if we'll see more Qt based DEs now... I just can't imagine them being as good as KDE though but I can't wait to see what they come out with! :)

---

### Post by Namtabmai on 2009-09-19
> **hoppipolla said:**
> So when did it become totally "free"? ^_^

June 2005.

And yes it's been 4 years, but there are a lot of application that have been around since then using GTK and even if Qt is a much better API I can't see the majority of them rewriting code to change over.

---

### Post by bruce89 on 2009-09-19
It's been a while since I've posted here, but I feel compelled to.

You can't compare Qt to GTK+. Qt is a complete development environment which abstracts a fair old bit over C++ (not literally I know).

GTK+ on the other hand is just a GUI toolkit. Nothing more, nothing less. For anything else, you need other libraries in the GNOME platform (libsoup, clutter, libxml2 etc).

GTK+ in C is verbose because of the fact that C is not object oriented. GObject has bolted object orientation on to C.

Also the fact that the GNOME developers actually do GTK+ as well means that they can put things in GTK+ if they need to.

Saying that Qt is better because the "Hello world" application is smaller is a false assertion. For the record, a GTK+ hello world could be done with next to no code using GtkBuilder.

---

### Post by hoppipolla on 2009-09-19
> **Namtabmai said:**
> June 2005.

And yes it's been 4 years, but there are a lot of application that have been around since then using GTK and even if Qt is a much better API I can't see the majority of them rewriting code to change over.

They don't need to rewrite the code though, I mean to be totally honest usually a new project comes together.

Amarok will I feel replace projects like Rhythmbox and Banshee. Kopete may be the one to replace Empathy/Pidgin (although the devs have gotten lazy recently so it may need a revamp). S/KMPlayer will replace Totem. KMail will replace Evolution, etc etc etc :)

---

### Post by bruce89 on 2009-09-19
> **hoppipolla said:**
> Amarok will I feel replace projects like Rhythmbox and Banshee. Kopete may be the one to replace Empathy/Pidgin (although the devs have gotten lazy recently so it may need a revamp). S/KMPlayer will replace Totem. KMail will replace Evolution, etc etc etc :)

As long as GNOME exists, this will never happen.

---

### Post by hoppipolla on 2009-09-19
> **bruce89 said:**
> As long as GNOME exists, this will never happen.

I may hold you to that :)


EDIT -- Oh and sorry don't get me wrong, by REPLACE I didn't mean the old projects will cease to be, I mean that they will replace them in like, mainstream use and may be chosen over the Gnome apps by distributions.

---

### Post by bruce89 on 2009-09-19
> **hoppipolla said:**
> I may hold you to that :)

Considering that Novell, Red Hat, Canonical (to an extent) and many other companies are backing it; this really is impossible.

---

### Post by hoppipolla on 2009-09-19
> **bruce89 said:**
> Considering that Novell, Red Hat, Canonical (to an extent) and many other companies are backing it; this really is impossible.

I may hold you to... :-#

hehe :)

---

### Post by Namtabmai on 2009-09-19
> **hoppipolla said:**
> Amarok will I feel replace projects like Rhythmbox and Banshee.

It's possible, but those big GTK applications have got a good foot hold by now. I mean what Qt application do you see replacing Gimp, Firefox, Eclipse, Open office, etc?

Notice these are all programs that have made it big on both Windows and Linux, they won't be just replaced any time soon.

---

### Post by p_quarles on 2009-09-19
> **Namtabmai said:**
> It's possible, but those big GTK applications have got a good foot hold by now. I mean what Qt application do you see replacing Gimp, Firefox, Eclipse, Open office, etc?

Notice these are all programs that have made it big on both Windows and Linux, they won't be just replaced any time soon.
Firefox and OpenOffice.org are not not GTK+ applications.

---

### Post by Namtabmai on 2009-09-19
> **p_quarles said:**
> Firefox and OpenOffice.org are not not GTK+ applications.

What?

I said they are GTK applications, and they are. Sure Openoffice has a KDE integration but it still depends on GTK.

---

### Post by larky on 2009-09-19
> **p_quarles said:**
> Firefox and OpenOffice.org are not not GTK+ applications.


aye

---

### Post by RiceMonster on 2009-09-19
> **Namtabmai said:**
> What?

I said they are GTK applications, and they are. Sure Openoffice has a KDE integration but it still depends on GTK.

They're made to follow GTK themes, but they are not actually written with gtk

---

### Post by bruce89 on 2009-09-19
> **Namtabmai said:**
> I said they are GTK applications, and they are. Sure Openoffice has a KDE integration but it still depends on GTK.

They are not GTK+ applications in the literal sense, they both use compatiblity layers (XUL and whatever OOo uses).

I am by no means a major GNOME contributor, but it's interesting to note that those who do work on KDE and GNOME do not flame each other. Only trouble makers such as the OP of this thread who do not do any work make a fuss.

This thread does not deserve any serious consideration.

---

### Post by Namtabmai on 2009-09-19
> **RiceMonster said:**
> They're made to follow GTK themes, but they are not actually written with gtk

Really then why do the Ubuntu/Debian packages for [Firefox](http://packages.ubuntu.com/jaunty/firefox-3.5) and [OpenOffice](http://packages.ubuntu.com/jaunty/openoffice.org-core) depend on GTK?

---

### Post by bruce89 on 2009-09-19
Never mind, read beyond this.

---

### Post by p_quarles on 2009-09-19
> **Namtabmai said:**
> What?

I said they are GTK applications, and they are. Sure Openoffice has a KDE integration but it still depends on GTK.
That is incorrect. Firefox uses the cross-platform XUL toolkit (also used by other Mozilla applications, as well as Songbird), and OOo uses native toolkits on each platform. The Linux builds of both inherit the looks of the GTK+ settings, but the larger point you were making (that these applications are tied to GTK+) isn't true.

---

### Post by hoppipolla on 2009-09-19
> **bruce89 said:**
> They are not GTK+ applications in the literal sense, they both use compatiblity layers (XUL and whatever OOo uses).

I am by no means a major GNOME contributor, but it's interesting to note that those who do work on KDE and GNOME do not flame each other. Only trouble makers such as the OP of this thread who do not do any work make a fuss.

This thread does not deserve any serious consideration.

o.O Then why post so much in it?

---

### Post by bruce89 on 2009-09-19
> **hoppipolla said:**
> o.O Then why post so much in it?

Very good point, bye.

---

### Post by hoppipolla on 2009-09-19
> **bruce89 said:**
> Very good point, bye.

Fair enough o.O

And to your original post before you edited it.. I never said you shouldn't be on the forum, and I never said I didn't care :S

---

### Post by bruce89 on 2009-09-19
> **hoppipolla said:**
> And to your original post before you edited it.. I never said you shouldn't be on the forum, and I never said I didn't care :S

Don't worry, I didn't think that.

---

### Post by keiichidono on 2009-09-19
Thanks for the kind words Bruce! I could have asked *if* Qt was better than GTK+ but inciting anger on both sides has allowed me to get more opinions and knowledge. I want to know the user/programmer positives and negatives of both Qt and GTK+ more in depth than what GeneralZod and phrostbyte have already provided if anyone is able to step up to the plate.

---

### Post by purgatori on 2009-09-19
Too bad most of the good applications are written in GTK2+; the graphical ones, anyway.

---

### Post by tcoffeep on 2009-09-19
> **CJ Master said:**
> GTK sucks. There, I stated my personal opinion with no reasons behind it. The world is better for that, right?

There ya go. Feel better?

(A note : I don't code in either. I prefer GTK apps over QT apps. That is all. Then again, when I require a QT app [like mudlet, which is developed in QT], I need to compile an assortment of QT libraries to use the app. In general, mind you. Every other app I've ever used is GTK. For example, here are my apps dependencies :

```

app-crypt/pinentry-0.7.5 (gtk? x11-libs/gtk+:2)
app-editors/gvim-7.2.182 (!aqua & gtk? >=x11-libs/gtk+-2.6)
app-text/evince-2.24.2 (>=x11-libs/gtk+-2.10)
app-text/ghostscript-gpl-8.64-r3 (gtk? >=x11-libs/gtk+-2.0)
app-text/gtkspell-2.0.15 (>=x11-libs/gtk+-2)
dev-cpp/gtkmm-2.12.7 (>=x11-libs/gtk+-2.12)
dev-libs/poppler-glib-0.10.7 (cairo? >=x11-libs/gtk+-2.14.0:2)
dev-python/gnome-python-base-2.22.3 (>=x11-libs/gtk+-2.6)
dev-python/gnome-python-desktop-base-2.24.1 (>=x11-libs/gtk+-2.4.0)
dev-python/pygtk-2.14.1-r1 (>=x11-libs/gtk+-2.13.6)
dev-ruby/ruby-gdkpixbuf2-0.16.0 (>=x11-libs/gtk+-2)
dev-ruby/ruby-gtk2-0.16.0-r4 (>=x11-libs/gtk+-2)
gnome-base/gail-1000 (>=x11-libs/gtk+-2.13.0)
gnome-base/gconf-2.24.0 (>=x11-libs/gtk+-2.8.16)
gnome-base/gnome-keyring-2.22.3-r1 (>=x11-libs/gtk+-2.6)
gnome-base/libglade-2.6.4 (>=x11-libs/gtk+-2.8.10)
gnome-base/libgnomecanvas-2.20.1.1 (>=x11-libs/gtk+-2.0.3)
gnome-base/libgnomeprintui-2.18.3 (>=x11-libs/gtk+-2.6)
gnome-base/librsvg-2.22.3 (>=x11-libs/gtk+-2.6)
mail-client/mozilla-thunderbird-2.0.0.23 (>=x11-libs/gtk+-2.8.6)
media-video/nvidia-settings-180.60 (>=x11-libs/gtk+-2)
media-video/vlc-0.9.10 (pda? x11-libs/gtk+:2)
net-im/pidgin-2.5.9-r1 (gtk? >=x11-libs/gtk+-2.0)
net-libs/webkit-gtk-1.1.10 (>=x11-libs/gtk+-2.10)
net-libs/xulrunner-1.9.0.14 (>=x11-libs/gtk+-2.8.6)
sys-devel/gcc-4.3.3-r2 (!build & gcj & gtk? >=x11-libs/gtk+-2.2)
www-client/mozilla-firefox-3.0.14 (>=x11-libs/gtk+-2.8.6)
www-client/uzbl-9999 (>=x11-libs/gtk+-2.14)
www-plugins/adobe-flash-10.0.32.18 (amd64 & !multilib? x11-libs/gtk+:2)
                                   (amd64&multilib&64bit? x11-libs/gtk+:2)
                                   (x86? x11-libs/gtk+:2)
x11-libs/gksu-2.0.2 (>=x11-libs/gtk+-2.4.0)
x11-libs/gtksourceview-1.8.5-r1 (>=x11-libs/gtk+-2.8)
x11-libs/libgksu-2.0.9 (>=x11-libs/gtk+-2.4)
x11-libs/wxGTK-2.8.10.1-r1 (X? >=x11-libs/gtk+-2.4)
x11-misc/nitrogen-1.4-r1 (>=x11-libs/gtk+-2.10)
x11-misc/pcmanfm-0.5.1 (x11-libs/gtk+:2)

```

And here are QT dependencies : (however, they were not compiled with the QT use flag)

```

app-crypt/pinentry-0.7.5 (qt3? x11-libs/qt:3)
app-text/djvu-3.5.21_p20090103 (qt3? x11-libs/qt:3)

```

So. Given the above. The apps I use are generally QT-free, and I've never seen a need to use a QT item. Aside from Mudlet, which is in beta, and I tend to use Tinyfugue, a terminal app, while Mudlet is not at a non-beta stage. So... Tell me, why should I hold any other opinion? Why should I put forward some form of proof? I am a user, not a developer.)

---

### Post by hoppipolla on 2009-09-19
> **purgatori said:**
> Too bad most of the good applications are written in GTK2+; the graphical ones, anyway.

That's true, but in my personal opinion it's only because KDE 4.x  has been a bit lame up until now. Now that we have a good, solid, impressive release of KDE 4 up and running (and that will continue to improve over time), I think that the Qt-based apps will gradually receive more TLC :)

---

### Post by wersdaluv on 2009-09-19
> **earthpigg said:**
> fair enough.

glad i put the 'i know i dont know wtf i am talking about' disclaimer in my first post.

sometimes, the quickest way to learn is to stir up the pot.
That's the nice tech guy attitude. 

I love your arguments.

---

### Post by earthpigg on 2009-09-19
> **wersdaluv said:**
> That's the nice tech guy attitude. 

I love your arguments.

designed to elicit a response i will learn something from.

"good sir, what is your opinion on the particular matter of ______?"

...elicits less of a response. 

objective was to learn. all else secondary.

---

### Post by wersdaluv on 2009-09-20
> **earthpigg said:**
> designed to elicit a response i will learn something from.

"good sir, what is your opinion on the particular matter of ______?"

...elicits less of a response. 

objective was to learn. all else secondary.
Yes. I'm in the same position now. I don't code but years playing with Linux gave me an idea on what those tooltips are.

So far, I can't tell which is really superior and if there will ever be a good enough criteria to define which is better than the other. Like you, my judgement would be based on the apps I use. Mozilla chose XUL to integrate with GTK+ and the same thing goes with other apps a user like me would care for like OpenOffice.org and Chrome/Chromium. Other than those, the apps that I can't do away with are Pidgin, GNOME Do, Tomboy, Virtualbox, and VLC. The last two on my list are Qt but they're not as important to me than Firefox and Pidgin. After all, they look nicely on my desktop because of QGtkStyle while my GTK+ apps can't mock my Qt style as good. 

Other than the apps I use, look and feel is a major consideration to me. As far as my taste is concerned, Oxygen probably is the best widget theme that I have ever seen on Linux apps. Ever since, I always preferred KDE's look (even in KDE3) over GTK+'s. It's just great because we have Nimbus, Shiki-Colors, and Sonar to satisfy my urge for desktop aesthetics.

Right now, I can't really choose between the two and I don't think if I will ever have the right to. I'm just sticking to GTK+ (for now) because Canonical has been polishing a great GNOME-based distro and the apps I care for are on GTK+.

---

### Post by phrostbyte on 2009-09-20
> **p_quarles said:**
> That is incorrect. Firefox uses the cross-platform XUL toolkit (also used by other Mozilla applications, as well as Songbird), and OOo uses native toolkits on each platform. The Linux builds of both inherit the looks of the GTK+ settings, but the larger point you were making (that these applications are tied to GTK+) isn't true.

On Linux, Firefox does use GTK+ and Cairo for drawing, AFAIK this is not a soft dependency. There was an attempt to port Firefox to Qt, I am not show how that ended up.

---

### Post by GeneralZod on 2009-09-20
To further clarify on the "OO.o and Firefox are not GTK" thing: these huge apps (together, they have more lines of code than most of the apps/ libraries in KDE's svn put together) run, without loss of functionality, on Windows, where they do not use GTK at all.  It's clear that the portions of the codebase that benefit from the use of GTK must be very small indeed and that GTK can be replaced completely without too much effort.

---

### Post by wersdaluv on 2009-09-20
> **GeneralZod said:**
> To further clarify on the "OO.o and Firefox are not GTK" thing: these huge apps (together, they have more lines of code than most of the apps/ libraries in KDE's svn put together) run, without loss of functionality, on Windows, where they do not use GTK at all.  It's clear that the portions of the codebase that benefit from the use of GTK must be very small indeed and that GTK can be replaced completely without too much effort.
Whether or not they can be ported easily, what matters is if they're ported. I would love to see firefox on qt so it would look nice whenever I'm on kde

---

### Post by hoppipolla on 2009-09-20
I think we should write some kind of song.

---

### Post by keiichidono on 2009-09-20
> **hoppipolla said:**
> I think we should write some kind of song.

Why?

---

### Post by Starlight on 2009-09-20
> **CalvinB said:**
> Why?

Because songs are good, I guess :)

And I'd love it if they made a Qt version of Firefox. They were trying to do it some time ago, there was even some early alpha version of Firefox 3 using Qt. It looked like... something very bad :P but it worked, so it was a good start :) I hope they are still making it.

---

### Post by wersdaluv on 2009-09-20
The discussion is civil enough :) This shows the maturity of UF. <3 it! :)

---

### Post by hoppipolla on 2009-09-20
> **Starlight said:**
> Because songs are good, I guess :)

I dunno the idea of a song about Qt just made me smile lol :)

---

### Post by GeneralZod on 2009-09-20
> **hoppipolla said:**
> I dunno the idea of a song about Qt just made me smile lol :)

Disclaimer: I have never actually watched this (and, hopefully, I never will :)) so I don't know if there is an actual Qt song in there.  Not for the easily embarrassed ;)

[http://www.youtube.com/watch?gl=BR&hl=pt&v=NbTEVbQLC8s](http://www.youtube.com/watch?gl=BR&hl=pt&v=NbTEVbQLC8s)

---

### Post by hoppipolla on 2009-09-20
> **GeneralZod said:**
> Disclaimer: I have never actually watched this (and, hopefully, I never will :)) so I don't know if there is an actual Qt song in there.  Not for the easily embarrassed ;)

[http://www.youtube.com/watch?gl=BR&hl=pt&v=NbTEVbQLC8s](http://www.youtube.com/watch?gl=BR&hl=pt&v=NbTEVbQLC8s)

"Do the Qute-four dance!" xD

EDIT -- Being a Qt programmer looks so much fun!! lol

---

