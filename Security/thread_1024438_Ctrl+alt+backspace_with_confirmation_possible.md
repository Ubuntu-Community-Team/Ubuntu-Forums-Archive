---
title: "Ctrl+alt+backspace with confirmation possible?"
date: 2008-12-29
forum: Security
---

### Post by Uji-Wu on 2008-12-29
Hi

I learned ctrl+alt+backspace to reset the x server, while configuring nvidia settings manager following instructions on a thread. It directly closed all applications. I am glad that i found this particular command, it shall become useful, but i thought i wouldnt quite like to do the same command while working on some hard art with the gimp, accidently. Or at any other possible activities. So, my question is: "would it be possible to add some comfirmation dialog box to the alt+ctrl+backspace key combinaison?" (Even if X is deep under all the rest of ubuntu... Like, i guess, one of linux's cores...)

The idea is more for general users and misc happenings than with me and my own self. I shall be ok with the command but someone could fall on the same key chain and lose documents, one day.. :) That's more the point. Altruism :P
thanx

-Leopold-François Depardieu 
-(mfhsbtj)

---

### Post by ushimitsudoki on 2008-12-29
You can *disable* it with:
> Option &#8220;DontZap&#8221; &#8220;yes&#8221;

In the "ServerFlags" section.

I don't think there is a way to ask for confirmation ... nor should there be. The purpose is not to close all applications. The purpose is to re-set the X server itself, which means there is a problem. It's not a thing you should be doing on a regular basis.

It's pretty unlikely someone is going to "accidentally" hit CTRL+ALT+BACKSPACE.

---

### Post by koenn on 2008-12-29
> **ushimitsudoki said:**
> 
I don't think there is a way to ask for confirmation ... nor should there be. ... The purpose is to re-set the X server itself, which means there is a problem. 
I agree. You'd use it when your X server / display manager / window manager is crashing. That's not the time you want to ask it to produce yet another dialog box.

---

### Post by ruchi on 2008-12-29
thanks for your posts its a new information for me.and its great information so thanks again.:KS

---

### Post by Uji-Wu on 2008-12-29
hmm... if i can disable it, mayby could i also change the key combination? Something as Lshift+ctrl+"windows+Rshift+delete would be more appropeiate for such a reset sequance :P ( when i try a new application, i always try my best to find all keyboard shortcuts and quick control moves )

A confirmation window could delay the x shutdown by 15 seconds, say something as "shutting down X server in "time"" and have a cancel button at its bottom.... But well.... Who cares, realy:P (not as if it was any priority) hehe

---

### Post by hyper_ch on 2008-12-30
> **ushimitsudoki said:**
> It's pretty unlikely someone is going to "accidentally" hit CTRL+ALT+BACKSPACE.
I tend to disagree... newly-converts might just press that combo out of old windows habits to start the task manager...

But then, if your system is so crippled that you can't even "click the log out buttons" anymore, then you really don't want any more confirmation before xserver gets resetted.

---

### Post by mikewhatever on 2008-12-30
> **hyper_ch said:**
> I tend to disagree... newly-converts might just press that combo out of old windows habits to start the task manager...

But then, if your system is so crippled that you can't even "click the log out buttons" anymore, then you really don't want any more confirmation before xserver gets resetted.

Wasn't it alt+ctrl+del that started the task manager in windows?

---

### Post by hyper_ch on 2008-12-30
didn't I just say that?

---

### Post by Uji-Wu on 2009-01-10
Untill i learned this ctrl+alt+backspace function i made myself to it. Its pretty useful tho! Its like a quick logoff :P

Yet... If i use it all the time as a logoff replacement that wont ever cause leaks right?

Talking logoffs... The hibernate function used to work but yesterday it made some crazy nonestop 2 error lines repeating.... Seems that was first and last time i could enjoy the power of hibernation:P hah......

so yeah, is ctrl+alt+backspace always safe, all the times?

---

### Post by ushimitsudoki on 2009-01-10
Ctrl+Alt+Backspace is **not** a "quick logoff".

No it is **not** "always safe, all the times."

Don't use it to logoff. That's not what it is for. Use it to kill X if needed - like if you lose input devices, monitors go wonky, system locks up or things like that.

If you want a keyboard shortcut to logoff, set one up. Don't use Ctrl-Alt-BkSp

---

