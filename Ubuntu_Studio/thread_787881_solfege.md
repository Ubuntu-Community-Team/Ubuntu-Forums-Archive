---
title: "solfege"
date: 2008-05-09
forum: Ubuntu Studio
---

### Post by tubunu on 2008-05-09
I've installed solfege through apt-get install but it just won't open. Here's the output in Terminal (which I can't figure out):

```
~$ solfege
Checking for gtkhtml2... ok
Solfege will use fakesynth
/usr/share/solfege/src/mainwin.py:436: GtkWarning: Refusing to add non-unique action '_Rhythm' to action group 'NotExit'
  self.m_action_groups['NotExit'].add_actions(actions)

Traceback (most recent call last):
  File "/usr/bin/solfege", line 77, in <module>
    src.mainwin.start_app(os.path.join(prefix, "share", "solfege"))
  File "/usr/share/solfege/src/mainwin.py", line 802, in start_app
    w.post_constructor()
  File "/usr/share/solfege/src/mainwin.py", line 640, in post_constructor
    self.m_app.display_sound_init_error_message(self.m_app.m_sound_init_exception)
  File "/usr/share/solfege/src/app.py", line 158, in display_sound_init_error_message
    self.m_ui.display_exception_message(e)
  File "/usr/share/solfege/src/mainwin.py", line 497, in display_exception_message
    sourcefile, lineno, func, code = traceback.extract_tb(sys.exc_info()[2])[0]
IndexError: list index out of range
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_solfege.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/solfege", line 77, in <module>
    src.mainwin.start_app(os.path.join(prefix, "share", "solfege"))
  File "/usr/share/solfege/src/mainwin.py", line 802, in start_app
    w.post_constructor()
  File "/usr/share/solfege/src/mainwin.py", line 640, in post_constructor
    self.m_app.display_sound_init_error_message(self.m_app.m_sound_init_exception)
  File "/usr/share/solfege/src/app.py", line 158, in display_sound_init_error_message
    self.m_ui.display_exception_message(e)
  File "/usr/share/solfege/src/mainwin.py", line 497, in display_exception_message
    sourcefile, lineno, func, code = traceback.extract_tb(sys.exc_info()[2])[0]
IndexError: list index out of range

```

Any workarounds? 
Much appreciated.

---

### Post by tubunu on 2008-05-10
:confused:

---

### Post by Stochastic on 2008-05-11
I just replicated the same error, looks like you've found a genuine bug.  Luckily it's already been filed at Launchpad (see [https://bugs.launchpad.net/ubuntu/+source/solfege/+bug/206093](https://bugs.launchpad.net/ubuntu/+source/solfege/+bug/206093)) and a workaround has been found: > I was able to run SOLFEGE with a little trick :

1) from the console, run solfege --no-sound :
    solfege starts (of course without sound)

2) inside solfege, do :
    "file" "preferences" "sound setup"

3) choose a midi setup that returns no error.
the first choice : "no sound" is the easiest choice !
On my system, i had to choose "use external midiplayer"

5) than save the changes, and exit.

6)Run solfege again from a console, from a desktop shortcut, or from a menu.

7) Et voila ! No crash, sound activated, enjoy the music !

I hope this helped!

Daniel


---

### Post by tubunu on 2008-05-19
Thanks a lot, that worked! :)

---

### Post by anotherone33 on 2008-06-06
thanks works. in my case xubuntu, and I had to change an option to ,,, external midi.
Next time all works from menu.

---

### Post by crazy757 on 2008-07-28
Okay, I understand to run solfege--no-sound.  I thought the console was the terminal, so I typed in solfege--no-sound and the terminal says command not found.  So, how do you run it without sound?  Thanks.

---

### Post by Stochastic on 2008-07-28
> **crazy757 said:**
> Okay, I understand to run solfege--no-sound.  I thought the console was the terminal, so I typed in solfege--no-sound and the terminal says command not found.  So, how do you run it without sound?  Thanks.

I bet you're forgetting the space between solfege and --no-sound.

---

### Post by crazy757 on 2008-07-31
Okay.  Thanks.  That worked perfectly for me.  I can't to start using it.  It will highly help me since I'm student teaching choir this Fall.

---

### Post by dansheldon on 2011-10-26
I cant get sound, dont know about tech issues and new to ubuntu, I downloaded Solfege but get this message;
"Module not detected
You should configure sound from the preferences window, and try to use an external midi player. Or try to recompile the program and check for error messages to see why the module is not built."
then it doesnt 'play' anything.
Like I said, Im not familiar even with where things are in ubuntu. Please help me with some simple instructions 
Cheers

---

