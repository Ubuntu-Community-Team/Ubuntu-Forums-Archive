---
title: "Combating a Virus in Windows"
date: 2011-01-27
forum: Security
---

### Post by Andrew Jeyaraj on 2011-01-27
Hi
A friend of mine has a virus on his WinXP system. His anti-virus (norton) couldn't do anything about it.

Details:
The virus creates a folder by the name of "new folder" whenever he uses windows explorer to open folders,drives etc. Also whenever he goes to google and searches for the word "anti-virus",his browser automatically closes. However,when i used "ninjaproxy" to use google and search for the keyword "anti-virus" nothing happened!!

So here's the problem. i booted puppyLinux of a live cd and tried deleting the virus wherever it came up.By the way its name is NewFolder.exe.
unfortunately this method did not work.

Should i boot ubuntu from a usb drive and try running avast? are there any other options?

what kind of virus is this??

cheers

---

### Post by kwacka on 2011-01-27
A quick look at google suggests that this has been around for a couple of years and there is a removal tool for Windows users.

---

### Post by Andrew Jeyaraj on 2011-01-27
yeah..i just checked.thanks..:)

but isnt there any way to do it through linux?

---

### Post by uRock on 2011-01-27
Here is the wiki on MS's Malicious Software Removal Tool, that should be included in the Windows user's monthly security updates from MS. [http://en.wikipedia.org/wiki/Windows_Malicious_Software_Removal_Tool](http://en.wikipedia.org/wiki/Windows_Malicious_Software_Removal_Tool)

To run the tool, click start, then run, then type ```
mrt.exe
```

You can also use the same command to run the tool from the command prompt.

---

### Post by uRock on 2011-01-27
> **Andrew Jeyaraj said:**
> yeah..i just checked.thanks..:)

but isnt there any way to do it through linux?
I recommend showing your friend how to use the tools that come with his or her system.

You may also want to instruct him/her to install Microsoft Security Essentials. It is free, easy to use and it doesn't eat resources while scanning. [http://www.microsoft.com/security_essentials/](http://www.microsoft.com/security_essentials/)


Edit: Moved to Security Discussions

---

### Post by Andrew Jeyaraj on 2011-01-27
ill try that
thanks a million:)

---

### Post by sneh_srijan on 2011-01-27
microsoft security essentials is effective only if ur windows is genuine.
you can try trojan remover also

---

### Post by uRock on 2011-01-27
> **sneh_srijan said:**
> microsoft security essentials is effective only if ur windows is genuine.
That is a good thing.:P I do not support pirating.

---

### Post by ssulaco on 2011-01-27
> **uRock said:**
> 
You may also want to instruct him/her to install Microsoft Security Essentials. It is free, easy to use and it doesn't eat resources while scanning. [http://www.microsoft.com/security_essentials/](http://www.microsoft.com/security_essentials/)

+1.....also I run Malwarebytes(safemode)....recommend deleting all but the most recent system restore snapshot,then run Malwarebytes in safemode.....malware likes to hide in system restore.

---

