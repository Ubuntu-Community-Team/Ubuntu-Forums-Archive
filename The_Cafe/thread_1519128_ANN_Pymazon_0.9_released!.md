---
title: "ANN: Pymazon 0.9 released!"
date: 2010-06-27
forum: The Cafe
---

### Post by sccolbert on 2010-06-27
I am happy to announce the 0.9 release of Pymazon. 

[http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/) 

Pymazon is a Python implemented downloader for the Amazon MP3 store. 

This release is a near-full rewrite which brings a brand new GUI design and a host of new features: 

Notably: 
- Pymazon now supports MP3 downloads which contain digital booklets and video attachments. 
- The GUI now has a settings dialog. No more having to manually edit the .pymazonrc file 
- An improved command line downloader interface. 
- A much much cleaner code-base. I wasn't happy with Pymazon the first time around, hence the rewrite. 
- Some convenience functionalities to mimic the official Amazon downloader. 

Pymazon can run on PyQt4, PyGtk, and the command line. 

This release is serving as the beta before the 1.0 release. 
I have done a fair bit of testing on this release, show it should be pretty stable. 
However, please report any bugs so I can fix them and tag the official 1.0 version. 

Aside from google code, Pymazon is also available in the cheese shop.

Cheers :guitar:

---

### Post by linnete on 2010-06-27
Hi sccolbert, I will check the link that you provided here to know more on this, I am not really familiar with it, but I am interested. Thanks

---

### Post by Bryan55 on 2010-07-12
Hi
i thought I had successfully installed Pymazon but when I tried to call it up I got this.

> bryan@Bydand:~$ pymazon
Traceback (most recent call last):
  File "/usr/local/bin/pymazon", line 67, in <module>
    main()
  File "/usr/local/bin/pymazon", line 41, in main
    main(amzs)
  File "/usr/local/lib/python2.6/dist-packages/pymazon/qt/ui.py", line 259, in main
    win = MainWindow(amzs)
  File "/usr/local/lib/python2.6/dist-packages/pymazon/qt/ui.py", line 118, in __init__
    loadFileIcon = QIcon.fromTheme('document-new', QIcon(QPixmap(load_icon_path)))
AttributeError: type object 'QIcon' has no attribute 'fromTheme'
bryan@Bydand:~$I can post a copy of what I did in the terminal to install it if that will help.

Thanks for any help.
Bryan

PS I'm fairly new to linux.

edit..Just realized that I may well have posted this in the wrong section please move if so.

---

