---
title: "GMail-Notifier for Ubuntu"
date: 2009-06-02
forum: The Cafe
---

### Post by uverma on 2009-06-02
Hello all,

I have been working on this new gmail-notifier for Ubuntu 9.04.  Its on version 0.4.5 now and is pretty stable.  It uses the new notification system to display e-mails (which I believe is pretty sweet looking) and looks a lot like the gmail notifier for Mac OS X.  

You can get it from here: [http://code.google.com/p/gmail-notifier/](http://code.google.com/p/gmail-notifier/)
A screenshot: [http://www.soundc.de/gmail-notifier/](http://www.soundc.de/gmail-notifier/)

Give it a try and let me know how it rolls :)

Thanks,
verma

---

### Post by burvowski on 2009-06-02
Looks good. Downloading now

edit: I'd like a bigger range for checking interval...or even better, just to input my own interval, instead of a max of 290 seconds.

---

### Post by Vostrocity on 2009-06-02
Thanks for telling us, even though most of us already know. I've tried it but don't like it because it notifies me of incoming mail that doesn't exist (too glitchy).

---

### Post by uverma on 2009-06-02
@burvowski

Thanks, point noted, for the next release I will provide such an option.

@Vostrocity

That's weird, initially I used the libgmail library which was indeed returning me e-mails that didn't exist.  However, now I am using the gmail atom feed for mail notifications, so this shouldn't happen.  Did you see those non-existant mails with version 0.4.5?

---

### Post by lovinglinux on 2009-06-02
It's very nice. Unfortunately, I can't make it open the inbox with Firefox. It launches Epiphany instead. How do I change that?

---

### Post by burvowski on 2009-06-02
> **lovinglinux said:**
> It's very nice. Unfortunately, I can't make it open the inbox with Firefox. It launches Epiphany instead. How do I change that?
system -> preferences -> preferred applications

---

### Post by lovinglinux on 2009-06-02
> **burvowski said:**
> system -> preferences -> preferred applications

](*,) The flu must be killing my brain. I went there before posting and didn't see the option right in front of me. Can you believe that? Everything is fine now. Thanks.

Edit: Strike that. It is still opening Epiphany.

---

### Post by Vostrocity on 2009-06-02
Oh just realized OP is the developer. Well I give it another shot, lemme see if I have the latest version.

---

### Post by GooglePlexity on 2009-06-02
I was going to say I wish there was an option to hide the notification area icon, but then I realized the context menu is highly functional.  Cool! nice job.

---

### Post by uverma on 2009-06-03
Thanks a lot everyone for trying it out.  

We have already started working on the next release for some new features.  The program will let you know once the update is available.

Thanks again,
verma

---

### Post by GooglePlexity on 2009-06-03
> **lovinglinux said:**
> ](*,) The flu must be killing my brain. I went there before posting and didn't see the option right in front of me. Can you believe that? Everything is fine now. Thanks.

Edit: Strike that. It is still opening Epiphany.

confirmed.  I think it's using gnome-www-browser, which for some reason still opens epiphany even when you've set firefox as your preferred browser through the configuration utility.

---

### Post by uverma on 2009-06-03
hmm .. noted.  I will look into this.  I am opening the www-browser to open the default web browser, but doesn't seem to be working as expected.  I will check how I can access preferred apps and use that.

Sorry about this, the next release will have the fix.

---

### Post by -grubby on 2009-06-03
It's not using gnome-www-browser, but x-www-browser. 

The code in launcher.py should be changed from:

```

def browser (url):
    launch ("x-www-browser", url)

```

to:

```

import webbrowser

def browser(url):
    webbrowser.open(url)

```

---

### Post by uverma on 2009-06-03
> **grubby- said:**
> It's not using gnome-www-browser, but x-www-browser. 

The code in launcher.py should be changed from:

```

def browser (url):
    launch ("x-www-browser", url)

```

to:

```

import webbrowser

def browser(url):
    webbrowser.open(url)

```


Oh sweet! .. I didn't know that package existed.  I will take a note of that and include it in the next build.

Thanks a lot :)

---

### Post by bekind2thenoob on 2009-06-03
I agree with burvowski's point about the refresh time, but other than that excelent! :)

---

### Post by indianinside on 2009-06-03
very nice looking .. works good ..

thanks

---

### Post by SomeGuyDude on 2009-06-03
My first thought: why not just go with the conky script?

My second though, upon seeing the screenshot: oh man that thing's slick.

I'm not on GNOME, but if all the kinks come out of it this should absolutely go into the Ubuntu repos.

---

### Post by uverma on 2009-06-03
Thanks guys :) .. I already have a list of issues from general use and feedback here:

[http://code.google.com/p/gmail-notifier/issues/list](http://code.google.com/p/gmail-notifier/issues/list)

which I will try to get done with before I release the next version.

@SomeGuyDude

I am really not sure how I can get this into Ubuntu repos (I would very much like to), would it be picked up by an Ubuntu developer? Or do I need to do something that will get this into Ubuntu repos?

---

### Post by Vostrocity on 2009-06-03
After using it for a while, I realized that it's not showing me nonexistant mail. It's just showing me old mail. Unlike some people, my inbox isn't squeaky clean. I have some accumulated mail from weeks or months ago that I haven't had time to open yet. :) I don't know if it's a feature or not to remind me of these old messages.

---

### Post by uverma on 2009-06-03
> **Vostrocity said:**
> After using it for a while, I realized that it's not showing me nonexistant mail. It's just showing me old mail. Unlike some people, my inbox isn't squeaky clean. I have some accumulated mail from weeks or months ago that I haven't had time to open yet. :) I don't know if it's a feature or not to remind me of these old messages.

I haven't really tested it with such a scenario.  If its annoying, tell me how would you want your mails to be presented? e.g. 20 most recent mails? or mails from last 30 days? or a setting which lets users set this?

With such huge storage accounts I think it may be pretty common for people to have old unread mails.  Off the top of my head, a configuration that lets you specify how recent mails to show could help.

I remember, once my gmail account had almost 1700 unread mails :).

Also, if its showing you mails that you don't want to see, you can always click on the notification icon for it to stop showing you notifications, from then on the program will only notify you about new  mails. This way you don't have to see notifications about emails which are an year old :).

I will note this issue down, and figure out a solution for this.

Thanks,
verma

---

### Post by hotweiss on 2009-06-03
I like it, just please add such options as Mark as Read, Delete, Report Spam, and Archive in the box. Something similar to what checkgmail has.

And make it so double-clicking on the icon opens your gmail account.

---

### Post by uverma on 2009-06-03
> **hotweiss said:**
> I like it, just please add such options as Mark as Read, Delete, Report Spam, and Archive in the box. Something similar to what checkgmail has.

And make it so double-clicking on the icon opens your gmail account.

hmmm .. I cannot really present those buttons you asked for because the notification mechanism doesn't allow you to place buttons on the new style notification mechanism, If I specify buttons, it switches back to dialog based notification system which looks really horrible and defeats the whole purpose.

I can however make it so that double clicking on the status icon makes it go to your gmail account.  Nice suggestion, thanks :)

---

### Post by Islington on 2009-06-04
> **uverma said:**
> hmmm .. I cannot really present those buttons you asked for because the notification mechanism doesn't allow you to place buttons on the new style notification mechanism, If I specify buttons, it switches back to dialog based notification system which looks really horrible and defeats the whole purpose.

I can however make it so that double clicking on the status icon makes it go to your gmail account.  Nice suggestion, thanks :)

this is fantastic. keep up the good work!

---

### Post by hotweiss on 2009-06-04
> **uverma said:**
> hmmm .. I cannot really present those buttons you asked for because the notification mechanism doesn't allow you to place buttons on the new style notification mechanism, If I specify buttons, it switches back to dialog based notification system which looks really horrible and defeats the whole purpose.

I can however make it so that double clicking on the status icon makes it go to your gmail account.  Nice suggestion, thanks :)

What about adding those buttons above the icon. For example, hovering (or even a single click) the mouse pointer over the mail icon displays those options and last email.

---

### Post by uverma on 2009-06-04
> **hotweiss said:**
> What about adding those buttons above the icon. For example, hovering (or even a single click) the mouse pointer over the mail icon displays those options and last email.

hmmm .. if you haven't already noticed, the notification area allows no interaction at all.  If you take your mouse over it, it will fadeout (or disappear altogether if not on compiz), so I cannot really put any interaction items on the notification window.  The notification mechanism is controlled by Ubuntu.

May be we could provide a submenu under every e-mail that marks the e-mails as read or unread or whatever.  But there is another problem with that.

I use the gmail atom feeds for getting information about new mails.  Although it would have been easier to do this with the older mechanism of checking emails, the older mechanism was quite buggy.  The new mechanism delivers information reliably, with direct links to e-mails, but provides no controls for manipulating mails in any way.

So with the current mail notification mechanism (presentation and fetch) there is really no straightforward way of doing this.  But may be we could do some hybrid approach, but I hope that doesn't complicate things too much.

---

### Post by hotweiss on 2009-06-04
> **uverma said:**
> hmmm .. if you haven't already noticed, the notification area allows no interaction at all.  If you take your mouse over it, it will fadeout (or disappear altogether if not on compiz), so I cannot really put any interaction items on the notification window.  The notification mechanism is controlled by Ubuntu.

May be we could provide a submenu under every e-mail that marks the e-mails as read or unread or whatever.  But there is another problem with that.

I use the gmail atom feeds for getting information about new mails.  Although it would have been easier to do this with the older mechanism of checking emails, the older mechanism was quite buggy.  The new mechanism delivers information reliably, with direct links to e-mails, but provides no controls for manipulating mails in any way.

So with the current mail notification mechanism (presentation and fetch) there is really no straightforward way of doing this.  But may be we could do some hybrid approach, but I hope that doesn't complicate things too much.

Thanks for the insight.

---

### Post by burvowski on 2009-06-04
I personally wouldn't prefer those extra button added. Simple is better IMO

---

### Post by Vostrocity on 2009-06-04
> **uverma said:**
> I haven't really tested it with such a scenario.  If its annoying, tell me how would you want your mails to be presented? e.g. 20 most recent mails? or mails from last 30 days? or a setting which lets users set this?

With such huge storage accounts I think it may be pretty common for people to have old unread mails.  Off the top of my head, a configuration that lets you specify how recent mails to show could help.

I remember, once my gmail account had almost 1700 unread mails :).

Also, if its showing you mails that you don't want to see, you can always click on the notification icon for it to stop showing you notifications, from then on the program will only notify you about new  mails. This way you don't have to see notifications about emails which are an year old :).

I will note this issue down, and figure out a solution for this.

Thanks,
verma

Yes right now it always gives me my 20 most recent. I prefer it to only remind me when there's a new incoming message. But it's no big deal. :)


> **burvowski said:**
> I personally wouldn't prefer those extra button added. Simple is better IMO
Yes I like it the way it is, just a simple notifier. If I need anything else I could just open up my browser.

---

### Post by uverma on 2009-06-04
> **burvowski said:**
> I personally wouldn't prefer those extra button added. Simple is better IMO

That's the whole idea I was going after.

---

### Post by uverma on 2009-06-04
> **Vostrocity said:**
> Yes right now it always gives me my 20 most recent. I prefer it to only remind me when there's a new incoming message. But it's no big deal. :)

The gmail atom feed must be controlling this then.  I haven't really put any such logic. Nice! :) 

The program will always shows you the mails you have in your account the first time you start it.  You can always click on the status bar icon for it to stop showing you the notifications.

---

### Post by treesurf on 2009-06-23
Is there any way to configure this so that it checks "All Mail" instead of just the Inbox?  This way it would pick up emails going to some of my other email accounts that Gmail handles for me.

---

### Post by treesurf on 2009-06-23
Ok, I've discovered that's it's possible for the Atom feed to also check different labels (which is how I have my other email accounts organized) by adding the name of the label to the Atom URL.  Is it possible to configure Gmail-notifier to check more then one Atom URL?

---

### Post by uverma on 2009-06-26
> **treesurf said:**
> Ok, I've discovered that's it's possible for the Atom feed to also check different labels (which is how I have my other email accounts organized) by adding the name of the label to the Atom URL.  Is it possible to configure Gmail-notifier to check more then one Atom URL?

Certainly sounds like a feature that could be helpful.  I will try to get this into the next build.  No promises though :) .. my list of features for the next build is pretty long as it is :).

---

### Post by moster on 2009-06-26
Uverma, thanks alot. I am looking for this too long. I've tried configuring pidgin, screenlets, some other things, nothing worked like I want. At last, BIG thanks for this little prog :D

---

### Post by treesurf on 2009-06-26
> **uverma said:**
> Certainly sounds like a feature that could be helpful.  I will try to get this into the next build.  No promises though :) .. my list of features for the next build is pretty long as it is :).


Thanks!

---

### Post by uverma on 2009-06-26
> **moster said:**
> Uverma, thanks alot. I am looking for this too long. I've tried configuring pidgin, screenlets, some other things, nothing worked like I want. At last, BIG thanks for this little prog :D

I am glad it could be of some use. :)

---

