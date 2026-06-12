---
title: "Picasa on Gazelle Pro with Ubuntu 14.04?"
date: 2014-07-11
forum: System76 Support
---

### Post by hkarl629 on 2014-07-11
I have a System 76 Gazelle Pro running Ubuntu 14.04 and would like to install Picasa on it.  Great computer!  Am familiar with Picasa from Windows computers which I now use infrequently  so feel the need to put Picasa on the new computer.

Did search on Ubuntu Software Center with no results.  Please tell me if Picasa will run under Ubuntu and where do I get it and how do I install it.

Thank you.

---

### Post by ajgreeny on 2014-07-11
Picasa 3.9 is no longer available directly for Linux but the last time I checked it ran very well in Wine.  I don't know if that is still the current situation, and I don't use Wine nor Picasa, but if you search I suspect you will find plenty of info, and you can also go to the wine [Wine Application DB]("http://appdb.winehq.org/") to see if it is listed there.

---

### Post by oldfred on 2014-07-11
I use Picasa in .wine, but do not connect to Google. And others have posted that as an issue. So if you want direct upload to Google you may have issues. 

I did have to update the IE in 12.04 after an update in Picasa to get upload to the photo site my wife uses to order prints. Have not tried to upload photos with 14.04 install yet as I have not fully converted to it. But install and updates worked.

[http://askubuntu.com/questions/86452/how-would-i-install-picasa-3-9](http://askubuntu.com/questions/86452/how-would-i-install-picasa-3-9)
[http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html](http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html)

You do have to install wine & winetricks first.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine winetricks

Then download picasa for windows
 ([http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe))
cd && wget [http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe)
Move it into .wine/drive_c/Program Files
Or if in /home then delete installer
wine ~picasa39-setup.exe
[EMAIL="fred@trusty-DT:~/.wine"]fred@trusty-DT:~/.wine[/EMAIL]/drive_c/Program Files$ wine picasa39-setup.exe

Some other links on issues:
[https://sites.google.com/site/picasaresources/Home/Picasa-FAQ/picasa/troubleshooting/picasa-won-t-upload-sync-to-web-or-gmail](https://sites.google.com/site/picasaresources/Home/Picasa-FAQ/picasa/troubleshooting/picasa-won-t-upload-sync-to-web-or-gmail)
env WINEARCH=win32 WINEPREFIX=~/.tmp winetricks ie8
wine 'C:\Program Files\Internet Explorer\iexplore'
C:\Program Files\Internet Explorer\iexplore

[https://sites.google.com/site/picasastartersite/other-tools/how-to-delete-duplicates#TOC-Check-for-and-Eliminate-Phantom-Duplicate-Folders](https://sites.google.com/site/picasastartersite/other-tools/how-to-delete-duplicates#TOC-Check-for-and-Eliminate-Phantom-Duplicate-Folders)

---

