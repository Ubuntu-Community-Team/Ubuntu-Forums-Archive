---
title: "Truecrypt"
date: 2014-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by anon_private on 2014-08-02
I can't see Truecrypt in the Software Centre.

Can this programme be installed?

Thanks

---

### Post by sudodus on 2014-08-02
> WARNING: Using TrueCrypt is not secure as it may contain unfixed security issues

according to the project's own web page at sourceforge

[http://truecrypt.sourceforge.net/](http://truecrypt.sourceforge.net/)

---

### Post by anon_private on 2014-08-02
> **sudodus said:**
> according to the project's own web page at sourceforge

[http://truecrypt.sourceforge.net/](http://truecrypt.sourceforge.net/)

Yes, I have read this.

I was using TC in Vista and have some encrypted volumes. If I transfer to Linux, I would like to gain access to the encrypted folders.

I will also need to check and see if UBUNTU supports the printer Lexmark Z2390, i.e. has a suitable driver.

Best wishes.

---

### Post by sudodus on 2014-08-02
Truecrypt is still available for this very reason (to save encrypted drives), but use it only for that purpose.

---

### Post by anon_private on 2014-08-02
> **sudodus said:**
> Truecrypt is still available for this very reason (to save encrypted drives), but use it only for that purpose.

I assume that it is available for Linux?

Reagrding the Red comment at the top. I find it difficult to distingusih between some chat and support. My questions are always seeking information. Information supplied is support as far as I am concerned.

Are there other Ubuntu etc support boards

---

### Post by sudodus on 2014-08-02
See at the end of this web page

[http://truecrypt.sourceforge.net/OtherPlatforms.html](http://truecrypt.sourceforge.net/OtherPlatforms.html)

I gave you the main page, and it is not too hard for you to look for the download links.

-o-

You must realize that this is no professional helpdesk, all of us are peers helping each other, volunteers. If you want professional help with Ubuntu, ask Canonical

[http://www.canonical.com/services](http://www.canonical.com/services)

or some local or regional linux or unix expert.

---

### Post by anon_private on 2014-08-02
> **sudodus said:**
> See at the end of this web page

[http://truecrypt.sourceforge.net/OtherPlatforms.html](http://truecrypt.sourceforge.net/OtherPlatforms.html)

I gave you the main page, and it is not too hard for you to look for the download links.

-o-

You must realize that this is no professional helpdesk, all of us are peers helping each other, volunteers. If you want professional help with Ubuntu, ask Canonical

[http://www.canonical.com/services](http://www.canonical.com/services)

or some local or regional linux or unix expert.

I am not interested in professional help

---

### Post by SuperFreak on 2014-08-02
[https://github.com/DrWhax/truecrypt-archive]("https://github.com/DrWhax/truecrypt-archive")
Supposedly these are the original zip files(For Win,Mac and Linux)and can be used for encryption as well as decryption. Use at own risk

---

### Post by sudodus on 2014-08-03
> **anon_private said:**
> I assume that it is available for Linux?

Reagrding the Red comment at the top. I find it difficult to distingusih between some chat and support. My questions are always seeking information. Information supplied is support as far as I am concerned.

Are there other Ubuntu etc support boards

> **anon_private said:**
> I am not interested in professional help

Do you want me to move your thread from this chat forum, where it is now, to our                                  [Security]("http://ubuntuforums.org/forumdisplay.php?f=338") forum? That might make it more visible to some security experts, and increase your chances to get relevant advice.

You can also search for advice at [http://askubuntu.com/](http://askubuntu.com/) I think it is easy to find relevant links via the general web search engine to Ask Ubuntu.

---

### Post by sudodus on 2014-08-03
> **anon_private said:**
> ...
I will also need to check and see if UBUNTU supports the printer Lexmark Z2390, i.e. has a suitable driver.

Best wishes.

Please open a new thread in the [Hardware]("http://ubuntuforums.org/forumdisplay.php?f=332") forum about printer support! Otherwise people who might be able to help you will probably not see it.

---

### Post by obake2 on 2014-08-03
Check here: [https://truecrypt.ch/](https://truecrypt.ch/)
That's the new homepage for truecrypt by the people who want it to be kept alive.


[http://www.infosecurity-magazine.com/view/38654/truecrypt-lives-on-as-new-team-relocates-to-switzerland/](http://www.infosecurity-magazine.com/view/38654/truecrypt-lives-on-as-new-team-relocates-to-switzerland/)

---

### Post by sudodus on 2014-08-03
> **obake2 said:**
> Check here: [https://truecrypt.ch/](https://truecrypt.ch/)
That's the new homepage for truecrypt by the people who want it to be kept alive.


[http://www.infosecurity-magazine.com/view/38654/truecrypt-lives-on-as-new-team-relocates-to-switzerland/](http://www.infosecurity-magazine.com/view/38654/truecrypt-lives-on-as-new-team-relocates-to-switzerland/)

Thank you for sharing this information :-)

---

### Post by vasa1 on 2014-08-03
> **anon_private said:**
> ...
Are there other Ubuntu etc support boards
I know the forum frowns upon things like LMGTFY but really it's always nice to show a little initiative 
even when asking a question.

---

### Post by mastablasta on 2014-08-04
Cyphershed? really? it doesn't make any sense...

is is chiffer, chypher something ... ugh difficult to remember. why shed?

---

### Post by SuperFreak on 2014-08-10
Veracrypt is another fork of [Truecrypt]("https://veracrypt.codeplex.com/") which is already available for Linux and Windows. Reportedly it has patched some of the shortcomings that the audit uncovered with Truecrypt. I know very little about it other than it is Open Source but seems to have a [Microsoft License]("https://veracrypt.codeplex.com/license")

---

### Post by uRock on 2014-08-10
For anyone who Googles with the intent of installing Truecrypt and manages to be reading this thread. 

The following three commands will get you Truecrypt.

```
sudo add-apt-repository ppa:stefansundin/truecrypt
sudo apt-get update
sudo apt-get install truecrypt
```If by any chance this doesn't work anymore, then please PM me. I'd like to know.

---

