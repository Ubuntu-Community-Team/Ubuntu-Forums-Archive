---
title: "Security certificate OK...but not for me :-("
date: 2008-08-27
forum: Security
---

### Post by ekh on 2008-08-27
Hi again

As I told in another thread I have been subject to attack 3 times.

[http://ubuntuforums.org/showthread.php?t=899529](http://ubuntuforums.org/showthread.php?t=899529)

First my server and the whole local net, then two times on one single portable used for accessing the net. I had to reinstall twice to get a seemingly stable system.

After 4 years with no trouble I'm now in paranoid mode, security wise.

I use Ossec to monitor my Ubuntu 8.04 desktop, and no problem indicated so far since last reinstall.

But a security certificate for a page is not OK for me. When my wife accesses the page at work, the certificate is OK, the same for my internet provider, for me it says:
  
[www.bilsyn.dk](www.bilsyn.dk) uses an invalid security certificate

The certificate for my netbank is OK.

You can check the certificate by accessing:

[http://www.applusbilsyn.dk/](http://www.applusbilsyn.dk/)

then click "Bestil tid" located top left

On the new page click the top picture with the text "Bestil online"

I expect you get no certificate warning.

My questions are: 

What can I do to make it work ?
Do I have a chance finding out if and who in case intercepts my communication ?

Thank you in advance, any help will be much appreciated.

ekh

---

### Post by Gamma746 on 2008-08-28
It works fine for me with Firefox 3.0.1.  What browser/version do you use?

---

### Post by ekh on 2008-08-28
I also use Firefox 3.0.1.

I tried the advice from cdenley in this thread:

[http://ubuntuforums.org/showthread.php?p=5679719#post5679719](http://ubuntuforums.org/showthread.php?p=5679719#post5679719)

Using Tor makes it work OK...But only for the first few pages, then it is broken.

So now my question:

"What can I do to make it work ?"

has been partly answered. But what about

"Do I have a chance finding out if and who in case intercepts my communication ?"

Now I know it is not a problem with the validation SW.

Are there tracing tools available that can trace the IP's of the communication chain ?

---

### Post by Gamma746 on 2008-08-28
> **ekh said:**
> Are there tracing tools available that can trace the IP's of the communication chain ?

Try using tracepath.

---

