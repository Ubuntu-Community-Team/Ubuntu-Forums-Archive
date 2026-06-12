---
title: "speech recognition to launch apps?"
date: 2007-08-02
forum: The Cafe
---

### Post by jgrabham on 2007-08-02
Is there a way that I can talk down my mic and it will launch apps if i say"launch firefox" etc?

---

### Post by TBOL3 on 2007-08-03
[http://www.voxforge.org/](http://www.voxforge.org/)

---

### Post by lixy on 2007-08-09
Perlbox worked like a charm last time I used it. It was specifically designed for that task.

[http://perlbox.org/](http://perlbox.org/)
[http://perlbox.sourceforge.net/](http://perlbox.sourceforge.net/)

---

### Post by lixy on 2007-08-09
Ok, I just installed Perlbox. In three years, it didn't evolve much but it's still very functional.

Anyway, the doc sucks. So, it took me five minutes to realize that to start it, you need to issue:

> perlbox-voice

Thought I'll save you the hassle...

---

### Post by popch on 2007-08-09
> **lixy said:**
> Ok, I just installed Perlbox. In three years, it didn't evolve much but it's still very functional.

Anyway, the doc sucks. So, it took me five minutes to realize that to start it, you need to issue:



Thought I'll save you the hassle...

Eh - do you have to SAY that?

---

### Post by tindallh on 2009-05-27
I'm having what appear to be Perl-Tk issues with Perlbox-voice under Jaunty (9.04); I can't select items in the listbox for "vocab"... Error reported is: 
> Tk::Error: Not a 
CODE reference at /usr/lib/perlbox-voice/Perlbox/ThirdParty/Tk/MListbox.pm line 703.
 Tk::Widget::Callback at /usr/lib/perl5/Tk/Widget.pm line 1149
 Perlbox::ThirdParty::Tk::MListbox::activate at /usr/lib/perlbox-voice/Perlbox/ThirdParty/Tk/MListbox.pm line 55
 Tk::Listbox::ButtonRelease_1 at ../blib/lib/Tk/Listbox.pm (autosplit into ../blib/lib/auto/Tk/Listbox/ButtonRelease_1.al) line 476
 <ButtonRelease-1>
 (command bound to event)

Anybody got any ideas?

---

### Post by Pasdar on 2009-05-27
Voice command sucks. Your throat will be dry at the end of the day and everything can be achieved much faster with keyboard and mouse.

---

