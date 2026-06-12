---
title: "Installing MoinMoin on Ubuntu for Beginners"
date: 2009-01-18
forum: Server Platforms
---

### Post by damormino on 2009-01-18
If you just want to try out MoinMoin on Ubuntu 8.10, the _best way_ is to download it from: [http://moinmo.in/MoinMoinDownload](http://moinmo.in/MoinMoinDownload)  and then install it as the DesktopEdition per [http://moinmo.in/DesktopEdition](http://moinmo.in/DesktopEdition)

If you want to install MoinMoin from Ubuntu's package management, be advised that many beginners quickly get frustrated with the lack of instructions on how to proceed once the package in installed.  Installing the package (called 'python-moinmoin) will not give you a running MoinMoin wiki.  Instead you will need to set up some things to get it running.

There are some useful threads installing MoinMoin from the package management:
[LIST]
[*][https://help.ubuntu.com/7.04/server/C/moinmoin.html](https://help.ubuntu.com/7.04/server/C/moinmoin.html)
[*][http://ubuntuforums.org/showthread.php?t=206850](http://ubuntuforums.org/showthread.php?t=206850)
[/LIST]

And here is how I got the python-moinmoin package mostly working on Ubuntu 8.10.

Installation:
The package 'python-moinmoin' typing 'sudo apt-get install -y python-moinmoin'.  One Ubuntu Desktop systems, it can be installed through the Synaptic Package Manager, or by opening a Terminal and typing 'sudo apt-get install -y python-moinmoin'

Quick Test:
Type 'moin server standalone', which will run moinmion.  (Type this in the Terminal if you are using Ubuntu Desktop).
In a web browser, enter 'http://localhost:8080'.
You will probably get a ConfigurationError, because (I think) the wiki instance has not be created.  In the terminal that you ran 'moin server standalone', type Ctrl-C to exit the server.  Proceed to configuration below.

Configuration:
<This needs to be written.> For now, see the page at [https://help.ubuntu.com/7.04/server/C/moinmoin.html](https://help.ubuntu.com/7.04/server/C/moinmoin.html) and try the configuration section.  That information is out-of-date and needs to be updated for Ubuntu 8.10.

You need to remember to restart MoinMoin with 'moin server standalone'

---

### Post by ShiftytheSpanner on 2010-09-23
G'day,

I followed your instructions and have set up a local wiki. Cheers it's working like magic. 

I want to be able to open files using their prescribed program from the wiki, e.g. click on a link and open a txt file using gedit , any ideas on where to start?? 

Thanks

---

