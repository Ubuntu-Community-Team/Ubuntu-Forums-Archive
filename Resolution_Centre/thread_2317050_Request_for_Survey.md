---
title: "Request for Survey"
date: 2016-03-13
forum: Resolution Centre
---

### Post by markdockendorf on 2016-03-13
Survey would be regarding usage of file servers and information regarding what features potential users might want in a graphical configuror for the vsftpd daemon.  The survey would close on Monday, March 21, 2016 .

(I did mistakenly post the survey before requesting permission, sorry about that.)
Questions would include:

Have you ever used a home or cloud-based FTP server before?
Have you ever wanted to make an FTP server for personal/home use?
What would you consider most important about an ftp server?
Have you ever set up an FTP server before? If not, go to question 8.
What server did you use?
Did you find it difficult to set up? Why or why not?
Would you consider your configuration complex (not in difficulty of setup, but complexity regarding the configuration the daemon was running)? How so?
Do you believe a graphical interface for configuring the server would be desirable? If not, why is it undesirable?
Would you expect the interface for configuring the file server to perform validation on the configuration (not just the data), or just write the data to the file? (ie. it listens on either IPv6 or IPv4)
Would you expect the configuration interface to allow configuration of users? (both virtual and local?)
Would you expect the configuration interface to handle mount points, set up raid volumes, and/or set up encrypted drives?
Would you expect the configuration interface to handle the options regarding FTP variants such as SFTP (FTP over SSH – encrypted usernames and passwords, but not data), FTPS (FTP over SSL/TLS implicitly– fully encrypted), and FTPES (FTP over SSL/TLS explicitly – client determines which portions of the conversation should be encrypted)? If so, would you expect to be able to change the SSL/TLScertificate via the interface?
Would you like to be able to manually choose encoding (for communication) or should it be set to a common, cross-platform encoding (such as UTF-8)?
Would you like the program be able to make backups of your current configuration before writing to the files?
Since this configuration tool will have to be run as root (in order to have the necessary authority to write to the configuration files) should the interface show a running log of actions taken by the program? By the user? If so, should it be always as verbose as possible, or should the verbosity be configurable?
Should the configuration tool be able to start/stop/restart the daemon (in order for the changes it makes to take effect)?
Should the package that the configuration tool comes in list vsftpd as a dependency (so that vsftpd is automatically installed with the configuration tool) or should it be standalone (so that the configuration tool's package can be removed after you're done using it to configure vsftpd)?
Would a settings *importer* (conf file &#8594; interface) be a high (in the first stable release), moderate (after the first fully-stable release), low (after everything else is fully complete), or non-priority for you?
Is there anything that you would like to see in a user interface to configure vsftpd other than the aforementioned potential features,network setup, path configuration, detailed tool-tips, and other basic configuration check boxes (for most of vsftpd's common boolean options)?

---

### Post by bapoumba on 2016-03-13
What would be the point of this survey ? Is this on the behalf of a public institution ? A private one ? Which one ? How will you use the user data ?

---

### Post by markdockendorf on 2016-03-13
> **bapoumba said:**
> What would be the point of this survey ?
To gather information from potential users regarding features they would like to see in a graphical configuration utility for vsftpd.

> **bapoumba said:**
> Is this on the behalf of a public institution ? A private one ? Which one ?
This would be on behalf of myself, the developer of said tool.

> **bapoumba said:**
> How will you use the user data ?
The data would be used to add features desired by the potential userbase of the program and prevent expenditure of time and effort for features that the users may find undesirable.

---

### Post by bapoumba on 2016-03-19
Thanks for answering and sorry it took a few days on my side to reply, work, you know.

That said, we would prefer an established ubuntuforum member posts such surveys. You have no history with us or Ubuntu that we can see. There are many other venues you can run surveys from, sorry.

Regards,
b.

---

