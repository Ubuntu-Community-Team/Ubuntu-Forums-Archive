---
title: "sha1sum mismatch! gdiplus"
date: 2009-10-02
forum: Wine
---

### Post by theswiffervac on 2009-10-02
i am trying to install gdiplus with winetricks, but whenever i try to, i get this
 
> peter@ubuntu:~$ sh winetricks gdiplus
sha1sum mismatch!  Rename /home/peter/.winetrickscache/./ppviewer.exe and try again.
i have read other threads on this, but they were talking about other apps, and it didnt really help. thanks for any help

I tried changing it to ppviewer.exe.broken, but i got this 

> Executing wget -O ppviewer.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/a/1/a/a1adc39b-9827-4c7a-890b-91396aed2b86/ppviewer.exe](http://download.microsoft.com/download/a/1/a/a1adc39b-9827-4c7a-890b-91396aed2b86/ppviewer.exe)
--2009-10-02 14:53:24--  [http://download.microsoft.com/download/a/1/a/a1adc39b-9827-4c7a-890b-91396aed2b86/ppviewer.exe](http://download.microsoft.com/download/a/1/a/a1adc39b-9827-4c7a-890b-91396aed2b86/ppviewer.exe)
Resolving download.microsoft.com... 208.111.156.188, 208.111.156.151
Connecting to download.microsoft.com|208.111.156.188|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-10-02 14:53:24 ERROR 404: Not Found.

Note: command 'wget -O ppviewer.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/a/1/a/a1adc39b-9827-4c7a-890b-91396aed2b86/ppviewer.exe](http://download.microsoft.com/download/a/1/a/a1adc39b-9827-4c7a-890b-91396aed2b86/ppviewer.exe)' returned status 1.  Aborting.


---

### Post by RobertHamilton on 2009-10-18
I have the same problem.. :(

Try removing ~/.wine and winetrickscache
then sh winetricks gdiplus and it'll reinstall everything

It didn't work for me though

> $ sh winetricks gdiplus
sha1sum mismatch!  Rename /home/robert/.winetrickscache/./WindowsXP-KB957096-x86-ENU.exe and try again.

---

