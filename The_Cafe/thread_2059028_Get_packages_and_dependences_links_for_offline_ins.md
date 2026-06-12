---
title: "Get packages and dependences links for offline install in Ubuntu website"
date: 2012-09-17
forum: The Cafe
---

### Post by tienlbhoc on 2012-09-17
Website: [http://ubuntuofflineinstall.com/](http://ubuntuofflineinstall.com/)

Don't like Windows or Mac, almost softwares in Ubuntu are provided with some packages and not good for offline install.
I made this website to solve this problem.
This website supports get packages and dependences links. This is content:


**Search with wildcard:**
%: Matches any number of characters, even zero characters
		_: Matches exactly one character 		Database based on original ubuntu (don't install or update any  packages), update  	  		every week. If you updated, some packages are  installed in your systems you still can 		use this database(redownload  and reinstall packages and dependences). 		


**How to install:**
		

[LIST]
[*]Download all packages, copy all to a folder
[*]Open terminal and cd to 		 		folder
[*]Type: sudo dpkg -i --force-depends *.deb
[/LIST]
 		Or can make script file with this context, set chmod +x for file, copy  script file to debs folder, double click -> run in terminal; copy  script file to other softwares and double click without type again

**How to download with DownThemAll (add on for firefox)**
 Search a package (example stardict): can download with many download manager  softwares
 [IMG]http://ubuntuofflineinstall.com/images/get%20stardict%20without%20md5.png[/IMG]  
Press Add MD5 check: only download with downthemall add-on in firefox browser  but can check md5 after download.
 [IMG]http://ubuntuofflineinstall.com/images/get%20stardict%20with%20md5.png[/IMG]  
Click to list, Ctrl+A to select all, choose a folder to save
 [IMG]http://ubuntuofflineinstall.com/images/Download%20them%20all%20options.png[/IMG]  
Download with md5 check
 [IMG]http://ubuntuofflineinstall.com/images/Download%20them%20all%20md5%20check.png[/IMG]

---

### Post by Jakin on 2012-09-17
Pretty useful in the event you cannot connect to the web :D

Would have been useful for me back on Dapper when i had a usb based modem, that Ubuntu just refused to recognize.. (oh but i'm pretty sure I did have it working when using LIVE CD :@)

---

### Post by tienlbhoc on 2012-09-17
Only for ubuntu 12.04 and newer (when have 12.10 my web will support it) because packages on ubuntu versions are differences

---

