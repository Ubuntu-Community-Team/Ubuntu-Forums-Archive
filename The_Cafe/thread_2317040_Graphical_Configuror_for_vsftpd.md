---
title: "Graphical Configuror for vsftpd"
date: 2016-03-12
forum: The Cafe
---

### Post by markdockendorf on 2016-03-12
So, after looking at all the ftp servers out there, I decided to go with vsftpd.  Here's the thing though, it's a pain to setup sometimes, so much so that I decided I would write a UI for configuring it.  I mean all that checking, double checking, documentation reading, etc. makes for a lot of reading.  Since I was going to go and do this, I wanted to know what other users thought about a UI for configuring it (*cough* and I kind of have to ask these questions as part of a class *cough*).

[LIST=1]
[*]Have you ever used a home or cloud-based FTP server before?
[*]Have you ever wanted to make an FTP server for personal/home use?
[*] What would you consider most important about an ftp server?
[*]Have you ever set up an FTP server before?  If not, go to question8.
[*]What server did you use?
[*]Did you find it difficult to set up?  Why or why not?
[*]Would you consider your configuration complex (not in difficulty ofsetup, but complexity regarding the configuration the daemon wasrunning)?  How so?
[*]Do you believe a graphical interface for configuring the server wouldbe desirable?  If not, why is it undesirable?[/FONT][/SIZE]
[*]Would you expect the interface for configuring the file server toperform validation on the configuration (not just the data), or justwrite the data to the file? (ie. it listens on either IPv6 or IPv4)
[*]Would you expect the configuration interface to allow configurationof users? (both virtual and local?)
[*]Would you expect the configuration interface to handle mount points,set up raid volumes, and/or set up encrypted drives?
[*]Would you expect the configuration interface to handle the optionsregarding FTP variants such as SFTP (FTP over SSH – encrypted usernames and passwords, but not data), FTPS (FTP over SSL/TLS implicitly– fully encrypted), and FTPES (FTP over SSL/TLS explicitly –client determines which portions of the conversation should beencrypted)?  If so, would you expect to be able to change the SSL/TLScertificate via the interface?
[*]Would you like to be able to manually choose encoding (forcommunication) or should it be set to a common, cross-platformencoding (such as UTF-8)?
[*]Would you like the program be able to make backups of your currentconfiguration before writing to the files?
[*]Since this configuration tool will have to be run as root (in orderto have the necessary authority to write to the configuration files)should the interface show a running log of actions taken by theprogram?  By the user?  If so, should it be always as verbose aspossible, or should the verbosity be configurable?
[*]Should the configuration tool be able to start/stop/restart thedaemon (in order for the changes it makes to take effect)?
[*]Should the package that the configuration tool comes in list vsftpdas a dependency (so that vsftpd is automatically installed with theconfiguration tool) or should it be standalone (so that theconfiguration tool's package can be removed after you're done usingit to configure vsftpd)?
[*]Would a settings *importer* (conf file &#8594; interface) be a high (in the first stable release),moderate (after the first fully-stable release), low (after everything else is fully complete), or non-priority for you?
[*]Is there anything that you would like to see in a user interface toconfigure vsftpd other than the aforementioned potential features,network setup, path configuration, detailed tool-tips, and otherbasic configuration check boxes (for most of vsftpd's common booleanoptions)?
[/LIST]
If you do decide to answer, please take it seriously, and thanks in advance.

---

### Post by cariboo on 2016-03-13
Aside from not using the default font, surveys must be approved by the Forum Council before they are posted:

> Surveys: Before posting your survey, please post a request in the Resolution Center. An administrator will respond to you to let you know if you can post it in the Ubuntu,Linux, and OS chat.
 

You can read the rest of the Forum Code of Conduct here:

[http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

Thread Closed

---

