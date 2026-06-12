---
title: "How To restore Firefox as default browser for Thunderbird"
date: 2011-10-17
forum: Tutorials
---

### Post by chandra on 2011-10-17
In Kubuntu 11.10, my default mail and browser applications are Thunderbird and Firefox respectively.

After installing Google Chrome (primarily for its integrated PDF viewing capabilities) I found that Thunderbird was suddenly opening http/https links in Google Chrome rather than Firefox.

After double checking that Google Chrome was **not** my default browser and that Firefox **was** my default browser, I still experienced the same behaviour.

After a search, I found this link that explained what happened in a Fedora setup:

[http://www.geeklab.info/2011/05/lovelock-mozilla-as-default-browser-from-thunderbird/](http://www.geeklab.info/2011/05/lovelock-mozilla-as-default-browser-from-thunderbird/)

I did what was advised there:

1. sudo edit /usr/share/applications/defaults.list

2. Change

```
[Default Applications]
text/html=google-chrome.desktop
text/xml=google-chrome.desktop
application/xhtml_xml=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/ftp=google-chrome.desktop
```

to

3.
```
[Default Applications]
text/html=firefox.desktop
text/xml=firefox.desktop
application/xhtml_xml=firefox.desktop
x-scheme-handler/http=firefox.desktop
x-scheme-handler/https=firefox.desktop
x-scheme-handler/ftp=firefox.desktop
```

Note that in Kubuntu it is firefox rather than mozilla-firefox that is the replacement string.

I do not know how this default setting happened in Kubuntu as gvfs-open is not installed. Anyway, the default was set in a sneaky fashion on my system without my explicit intervention, and I am grateful that David at GeekLab found out what had happened and how to fix it.

I hope this helps others.

---

### Post by BlakJakNZ on 2012-02-12
Thanks for posting this.  I was having similar problems (I run Ubuntu 10.10 with the Stable Thunderbird and Firefox PPAs) and hadn't been able to find much else useful til I found this thread.... 

That said my defaults.list didn't have the same stuff in it.

I'd simultaneously posted to the NZLUG and one of the contributors there suggested the following:
> 
That might be true. Use gconf-editor and check the following:   /desktop/gnome/url-handlers/http/   /desktop/gnome/url-handlers/https/

I checked these and whilst http was set up as 'firefox %s', https was set up with 'sensible-browser %s' (and running this called Chromium).

Changing it to Firefox appears to have resolved my problems.

Hope this is of assistance to others, thus my posting it here. Cheers.

---

### Post by cumanacr on 2012-03-16
Thanks, this solution works on kubuntu 12.04 as well.

---

### Post by BlakJakNZ on 2012-03-20
I just switched from Ubuntu 10.10 to Xubuntu 12.04. With no gconf-editor shipped (and seemingly a list of package dependencies a mile long when I looked at installing it) I took a different approach.  in /etc/alternatives I did this:
```
root@hawkeye:/etc/alternatives# ls -l | grep browser
lrwxrwxrwx 1 root root  25 Mar 14 20:50 gnome-www-browser -> /usr/bin/chromium-browser

(irrelevant lines removed)

lrwxrwxrwx 1 root root  25 Mar 14 20:50 x-www-browser -> /usr/bin/chromium-browser

root@hawkeye:/etc/alternatives# rm gnome-www-browser 
root@hawkeye:/etc/alternatives# rm x-www-browser 
root@hawkeye:/etc/alternatives# ln -s /usr/bin/firefox gnome-www-browser
root@hawkeye:/etc/alternatives# ln -s /usr/bin/firefox x-www-browser
```

This was provoked by having similar browser-inconsistency problems with links sent to me via Instant Messenger (pidgin).... they all seemed to open in chromium despite default-browser state being pointed at Firefox.

A bit hackery, but so far seems to work. Anyone aware of an equivalent to gconf-editor for Xfce?

---

### Post by NGSG on 2012-03-28
HI,
indeed the easiest solution is to simply do the following in Firefox:
Edit->Preference -> Advanced -> General -> Set Firefox as default (check now)
and restart Thunderbird.
no need of extra settings.
see you.

---

### Post by BlakJakNZ on 2012-03-28
Yeah, er, no... no such menu item.

My little hack stopped working after a couple of weeks, fortunately a local guru posted the following instructions onto [my blog]("http://www.blakjak.net/content/fun-xubuntu") in response to an article I posted:



```
  sudo update-alternatives --config x-www-browser
```

Perfect.

---

### Post by peredur on 2012-10-29
> **NGSG said:**
> HI,
indeed the easiest solution is to simply do the following in Firefox:
Edit->Preference -> Advanced -> General -> Set Firefox as default (check now)
and restart Thunderbird.
no need of extra settings.
see you.

Nice one.  That worked just fine for me.  Another annoying quirk ironed out. Thanks.

P

---

### Post by handsaway on 2013-02-15
> indeed the easiest solution is to simply do the following in Firefox:
Edit->Preference -> Advanced -> General -> Set Firefox as default (check now)Thank you so much NGSG!

You put an end to three hours of my trying to figure out how to make my IBM Lotus Notes open http links in Firefox and not Chromium.

In case that helps others, I had the following problem:

[LIST]
[*] My mail reader is Lotus Notes 8.5, configured to use the default OS web browser when opening links (in File>Preferences>Web Browser thumbnail).
[*]Firefox was set as the default web browser for the system (in System Settings>Details>Default Applications).
[*]I had verified that Firefox was the OS default web browser by running:
```
 sudo update-alternatives --config x-www-browser
```
[/LIST]
 And yet, Chromium would always pop up when clicking a http link in Lotus Notes...
I tried the solution explained [here]("http://ubuntuforums.org/showthread.php?p=11626516"), which involves editing the file 'defaults.list' (inverting Chrome/Chromium and Firefox to fit my case of course), but to no avail.

Your very simple solution corrected the problem.

---

### Post by gstanden on 2013-12-15
I also ran into this issue of having set Firefox as default in Settings-->Details and also set Firefox as default with update-alternatives.  I fixed by selecting "other" when the "what do you want to use to open this file" dialog popped up and navigating to "/usr/bin/firefox" which from then on firefox was always offered as the default option inthe "what do you want to use" dialog.  HTH, Gil

---

### Post by rf0 on 2014-09-14
Why is something so important in such disarray?

---

