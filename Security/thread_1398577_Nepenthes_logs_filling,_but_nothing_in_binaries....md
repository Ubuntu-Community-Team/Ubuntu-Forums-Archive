---
title: "Nepenthes logs filling, but nothing in binaries..."
date: 2010-02-04
forum: Security
---

### Post by panicy on 2010-02-04
I've been running nepenthes for about 3 days now and it seemed to work fine at first.  The first two logged attacks dropped binaries into /var/lib/nepenthes/binaries with the other info in /var/log/nepenthes/logged_downloads and logged_submissions that corresponded to to the md5 in downloads and submissions

But then since the first two attacks the binaries folder hasn't filled up with anything else BUT logged_downloads and logged_submissions continues to grow with logged attacks.  The strange thing also is that within the listed urls in logged_downloads it has a file at the end of the url (ie: mslaugh.exe) and it has md5 listed in submissions.       :confused:

So obviously nepenthes is still running, but what does that mean?  Is it that the attacks are trying to reach an ip/url that has been shutdown?

The logged attacks are of all types: tftp, creceive, ftp, and link.

when I run lsof -i, nep is listening on several services, so it seems as if all the .conf files are ok.  

Am I doing something wrong (my first honeypot...)?   It just seems strange that the first two worked as it should and then for the next two days... nothing

Any ideas would be great!
Thanks for reading!

---

