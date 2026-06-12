---
title: "Can gmail give ubuntu viruses?"
date: 2010-02-17
forum: Security
---

### Post by dogdo on 2010-02-17
Hello

I know that ubuntu is highly resistant to windows based viruses but what if I open a attachment or click on a link within a email that is infected with a linux or platform agnostic virus?

---

### Post by doas777 on 2010-02-17
before the gloom and doom, the short answer to your question, is that you are probably safe. just follow the basic rules, and ignore attachments from unknown addresses.

ok, you have to be careful with terminology. "viruses" are a specific type of malware. you should also consider Trojans, Worms, rootkits, and spyware.

viruses are almost unheard of on linux, but they are also quite rare nowadays in windows. haven't been a big problem since '05 (aka, the year of the trojan). 

worms are a theoretical problem, but you are very unlikely to come across one. rootkits are the most likely problem in linuxdom, but they too are quite rare on desktops (since who really wants to root your desktop, instead of a juicy server?). rootkits are usually a secondary sign that someone has hacked your system.

Trojans are a bigger deal however. yes if you download bad code from anywhere, and install it with admin privileges, then little or no additional security can save you.

Spyware is likely the biggest problem pertaining to webmail. most spyware does not use the underlying operating system to do their dirty work, instead using firefox to do it for them. in most cases, a javascript based spyware, will work as well on ubuntu as it will in windows.

so to sum up, linux is much more secure, but if you do somthing stupid, then there is little to save you.

hth

---

### Post by rookcifer on 2010-02-17
> **dogdo said:**
> Hello

I know that ubuntu is highly resistant to windows based viruses but what if I open a attachment or click on a link within a email that is infected with a linux or platform agnostic virus?

There are two possible scenarios:

1) If the virus is exploiting a flaw in an application like a browser or e-mail client, then simply clicking it could possibly allow it to infect your user account.  However, most Linux e-mail clients are very sane when it comes to handling attachments and HTML, etc.  You aren't going to see any craziness like we used to see years ago with Outlook when you could be pwned by merely opening an e-mail, nevermind the attachment.

2) The attack is not exploiting any flaw in the code, but is merely a malicious executable.  In this scenario, you will be safe even if clicking on the link or opening the attachment since the file cannot execute without further action on your part (like adding the "x" bit to the file).  Newly created (or downloaded) files are not executable by default on most Linux distros.  This is different from Windows where a file executes on its own.

---

