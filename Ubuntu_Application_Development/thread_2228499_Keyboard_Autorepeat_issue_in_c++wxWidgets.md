---
title: "Keyboard Autorepeat issue in c++/wxWidgets"
date: 2014-06-07
forum: Ubuntu Application Development
---

### Post by rompelstilchen on 2014-06-07
hello,

i am actually writting an app with wxwidget
(i already went to a wxWidget forum but people say the code works perfectly fine on Windows and Debian, ...but not on my Ubuntu box)

as the api allows to filter system to application events, i used this function 

```

int MyApp::FilterEvent(wxEvent& event)
{
    if(event.GetEventType()==wxEVT_KEY_DOWN)
        cout << "wxEVT_KEY_DOWN" << endl;
    else if(event.GetEventType()==wxEVT_KEY_UP)
        cout << "wxEVT_KEY_UP" << endl;
}

```

I get this :

wxEVT_KEY_DOWN
wxEVT_KEY_UP
wxEVT_KEY_DOWN
wxEVT_KEY_UP
wxEVT_KEY_DOWN
wxEVT_KEY_UP
wxEVT_KEY_DOWN
wxEVT_KEY_UP
wxEVT_KEY_DOWN
wxEVT_KEY_UP
wxEVT_KEY_DOWN
wxEVT_KEY_UP
wxEVT_KEY_DOWN
wxEVT_KEY_UP
wxEVT_KEY_DOWN
...

so it seems the system sends keys up and keys downs 
instead of only keys downs (and key up, once the keyboard key gets released)

i should get this:

wxEVT_KEY_DOWN
wxEVT_KEY_DOWN
wxEVT_KEY_DOWN
wxEVT_KEY_DOWN
wxEVT_KEY_DOWN
wxEVT_KEY_DOWN
wxEVT_KEY_UP


i wondered if someone had a clue what could cause this problem ?

thanks

---

### Post by rompelstilchen on 2014-06-08
anyone ?

this is really a system issue, i tried different codes that people affirmed to be working on windows ans other linux's

it seems the autorepeat is wrongly transmiting key events to applications in ubuntu 13.10

or maybe there is a special trick i am not aware of...

[edit: i also tried to disable the autorepeat feature in the keyboard settings, to see if i had some different behaviour, it does not work, autorepeat stays on]

---

### Post by rompelstilchen on 2014-06-10
please... guys, any advice is welcome
thx

---

### Post by steeldriver on 2014-06-10
It certainly seems like a keyboard autorepeat issue - what happens if you do

```

xev -event keyboard

```

in a terminal and then press and hold a key - does the behavior change if you do

```

xset r off

xev -event keyboard

```

---

### Post by rompelstilchen on 2014-06-11
i dont seem to get it right.. :-(

```

odroid@odroid:~$ xev -input keyboard
usage:  xev [-options ...]
where options include:
    -display displayname                X server to contact
    -geometry geom                      size and location of window
    -bw pixels                          border width in pixels
    -bs {NotUseful,WhenMapped,Always}   backingstore attribute
    -id windowid                        use existing window
    -root                               use root window
    -s                                  set save-unders attribute
    -name string                        window name
    -rv                                 reverse video
    -event event_mask                   select 'event_mask' events
           Supported event masks: keyboard mouse expose visibility structure
                                  substructure focus property colormap
                                  owner_grab_button randr
           This option can be specified multiple times to select multiple
           event masks.


```

---

### Post by rompelstilchen on 2014-06-11
i compared xset r (off and on) trying some keys in the terminal but autorepeat seems always on

---

### Post by steeldriver on 2014-06-11
oops sorry I meant

```

xev **-event** keyboard

```

---

### Post by rompelstilchen on 2014-06-11
yes i stil get a press AND release event with off option

---

### Post by steeldriver on 2014-06-11
Hmm.. well I tested it in a VM running a vanilla install of 13.10 Ubuntu Desktop and the 'xset r off' option appears to work as expected

I don't really know where to start looking for why yours is behaving differently

---

### Post by rompelstilchen on 2014-06-11
i know 

strange it never impacted the general usability of the whole system and programs

i posted a thread on Odroid forum, i'll see what they will say
they make their own brew of each Ubuntu release, so ... or maybe it's and hardware usb issue

thx anyway :-)

---

### Post by steeldriver on 2014-06-11
Well 'autorepeat ON' is the default behaviour - so I wouldn't expect that to be an issue for general usability. Your wxWindows code should be able to handle autorepeat - perhaps the issue here is that the delay value (the time interval before a single key press becomes interpreted as a key 'hold') is being misapplied?

However the fact that you apparently can't disable it with xset suggests there's something more general going wrong under the hood.

---

