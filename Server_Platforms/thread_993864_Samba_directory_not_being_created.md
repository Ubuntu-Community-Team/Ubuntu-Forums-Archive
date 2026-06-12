---
title: "Samba directory not being created"
date: 2008-11-26
forum: Server Platforms
---

### Post by happyhacker on 2008-11-26
I have just installed webmin on the server 8.10. When I create a new file share using webmin and try to create a dircectory neither the file list is available (the browser just flickers when I click the button) or a directory gets created under home. Samba in webmin does show a new [allusers] though under the config file.

I am trying to create one under my home dir but don't know if this is right. Everything else is default and I have no users and I am following:[this tutorial]("http://doxfer.com/Webmin/SambaWindowsFileSharing").

Any advice welcome. I have tried restarting samba and ubuntu.

---

### Post by dantrevino on 2008-11-26
webmin is not supported due to how it manages config files.  You should try ebox.

Read the "Introduction" section here: [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)

and ignore the rest.

dan

---

### Post by happyhacker on 2008-11-27
Hm, I see. My problem was a corrupted JAVA installation and when I reinstalled webmin file manager worked. So I have now used webmin and samba to get file sharing going. I do notice that if I try to use the Config facility of webmin file manager I get this message:

[COLOR="Red"][SIZE="1"]Warning! Webmin has detected that the program [https://192.168.0.2:10000/config.cgi?file](https://192.168.0.2:10000/config.cgi?file) was linked to from an unknown URL, which appears to be outside the Webmin server. This may be an attempt to trick your server into executing a dangerous command.
If your browser does not send the Referer header needed, you can turn off this check as follows :

Login to Webmin normally.
Go to the Webmin Configuration module.
Click on the Trusted Referrers icon.
Check the Trust links from unknown referrers box, and click Save.
Alternately, you can configure Webmin to allow links from unknown referers by :

Login as root, and edit the /etc/webmin/config file.
Find the line referers_none=1 and change it to referers_none=0.
Save the file.[/SIZE][/COLOR]

Is this what you are refering to?

---

### Post by rslrdx on 2008-11-28
the webmin error is just a config setting you may want to change... doesnt have anything to do with samba or anything else... its a security thing in webmin... just do the steps on the second paragraph.

---

