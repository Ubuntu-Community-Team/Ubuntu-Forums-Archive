---
title: "detected virus"
date: 2009-12-08
forum: Security
---

### Post by peskadot on 2009-12-08
Been running Ubuntu for about 6 months on dual boot (vista-ubuntu) system.  Never had a virus issue.  Began scanning with clam-tk a few weeks ago because of potential back-door windows infection.  Lately, Clam-tk has been finding infected files nearly every search.  Always in Firefox cache (.mozilla/firefox/vkuuxfit.default/Cache).  "PUA.Script.Packed-2" is a constant repeat.   

Is any one else experiencing this?  Is this a false positive?

---

### Post by bodhi.zazen on 2009-12-08
My advice to you, if you are wanting to use antivirus on Linux you need to learn to use google to search on the results .

For example:

[http://lmgtfy.com/?q=virus+PUA.Script.Packed-2](http://lmgtfy.com/?q=virus+PUA.Script.Packed-2)

:p

Which yields :

[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2009-11/msg01802.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2009-11/msg01802.html)[]("http://www.******************/ubuntu-user/280348-virus-alert.html")

[http://ubuntuforums.org/showthread.php?p=8381815](http://ubuntuforums.org/showthread.php?p=8381815)

I am not trying to be rude mind you, but such is the nature of Antivirus, IMO, both on Windows and Linux (you should always confirm your reported files to see what it is you are looking at exactly and what to do about it).

---

### Post by Penguinsunite on 2009-12-08
I have to agree with bodhi.zazen. I have been running ubuntu on my home computer for about the same amount of time, it's always connected to the internet and is usually running. I have never had a problem with a virus or runningg slow. The only thing i can think of is that your antivirus is returning a false positive. google whatever your antivrus says and doublecheck it on the internet and see what you get.

---

### Post by lisati on 2009-12-08
Clearing your browser cache from time to time is always an option, particularly if that's the only place the AV scanner is finding "suspicious" files.

---

### Post by teward on 2009-12-08
Or, configuring the internet browser to clear the cache automatically on exit is also a good idea.  I've set mine up to do that because the info sometimes stored in cache can be used in malicious ways (see?  case in point with your issue).

---

### Post by peskadot on 2009-12-09
Ask a simple question and expect a simple answer.  I did google PUA.Script.Packed-2 and got an answer similar to the ones provided here.  It may, or then again may not be, a malicious item.  It does appear to be uniquely associated with clam-tk and linux.  PUA stands for Probably Unintended Application - that's a big help. 

What is it with computer geeks?  Can you not speak in simple sentences?  If you don't know something, just say so.  If you do know, you don't have to show your superiority by being rude and not answering directly.

---

### Post by lisati on 2009-12-09
> **peskadot said:**
> Ask a simple question and expect a simple answer.  I did google PUA.Script.Packed-2 and got an answer similar to the ones provided here.  It may, or then again may not be, a malicious item.  It does appear to be uniquely associated with clam-tk and linux.  PUA stands for Probably Unintended Application - that's a big help. 

What is it with computer geeks?  Can you not speak in simple sentences?  If you don't know something, just say so.  If you do know, you don't have to show your superiority by being rude and not answering directly.

We're all volunteers here. Please go easy on us. Answering questions in a useful manner is a delicate balance between a short answer, maybe with some jargon, and a longer answer that assumes the person knows less than they probably do.

---

### Post by mikewhatever on 2009-12-09
I'd suggest reading Clamav FAQ.
[http://www.clamav.net/support/faq/pua/](http://www.clamav.net/support/faq/pua/)

```
PUA – Possibly Unwanted Applications...
```

It should be obvious after reading, that PUA is not a virus. In fact, rather useful categories like IRC and p2p are labeled as PUA.

---

### Post by bodhi.zazen on 2009-12-09
> **peskadot said:**
> What is it with computer geeks?  Can you not speak in simple sentences?  If you don't know something, just say so.  If you do know, you don't have to show your superiority by being rude and not answering directly.

First, while I understand you are frustrated, there is no need for you to be insulting.

Nothing in your post indicated you had even tried to answer your question. I suggest you take a look at this :

[http://catb.org/~esr/faqs/smart-questions.html](http://catb.org/~esr/faqs/smart-questions.html)

If you had posted something along the lines of :

clam-tk found a file foo and I did a google search and found it is a PUA, What is a PUA and what should I do ?

Or

I read this thread : [http://ubuntuforums.org/showthread.php?p=8381815](http://ubuntuforums.org/showthread.php?p=8381815) and do not understand xyz, would somebody please explain it to me ?

Nothing in your OP indicated you had done anything to research the problem nor that you had any question about what you had found.

We are not telepathic and if you expect us to provide you with better answers you should ask better questions.

Once you rephrased the question, mikewhatever gave you a better answer.

---

