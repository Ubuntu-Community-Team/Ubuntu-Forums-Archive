---
title: "my billing solution can't connet with my server"
date: 2007-02-03
forum: Server Platforms
---

### Post by cap10kirk on 2007-02-03
I use CCBill for my third party billing company. I have absolutly no problems with the server, except for this wierd issue with CCBill. They are telling me that they can't connect to the server because of a time out error. For whatever reason, they can't FTP on their end. I can FTP all day long. It's not a firewall problem. I have no clue. and they aren't helping either. Any ideas on what the problem could be?

Thanks in advance
Kirk

---

### Post by tturrisi on 2007-02-04
If your server is behind a router then you need to port forward 21.
Can they ssh to your server?

---

### Post by cap10kirk on 2007-02-05
I'm not sure if they can ssh it. The server is not behind a firewall. I did not install a software firewall. I use ISPConfig to make my virtual sites. Here is the error log:

 *** CuteFTP Pro 3.3 - build Aug 25 2003 ***

STATUS:>         Getting listing ""...
STATUS:>         Resolving host name [www.mysite.com](www.mysite.com)...
STATUS:>         Host name [www.mysite.com](www.mysite.com) resolved: ip = 12.34.56.789.
STATUS:>         Connecting to ftp server [www.mysite.com:21](www.mysite.com:21) (ip = 12.34.56.789)...
STATUS:>         Socket connected. Waiting for welcome message...
                  220 ProFTPD 1.3.0 Server (Debian) [::ffff:12.34.56.789]
STATUS:>         Connected. Authenticating...
COMMAND:>         USER web1_mysite
                  331 Password required for web1_mysite.
COMMAND:>         PASS *****
                  230 User web1_mysite logged in.
STATUS:>         Login successful.
COMMAND:>         PWD
                  257 "/var/www/web1" is current directory.
STATUS:>         Home directory: /var/www/web1
COMMAND:>         FEAT
                  211-Features:
                  MDTM
                  REST STREAM
                  SIZE
                  211 End
STATUS:>         This site supports features.
STATUS:>         This site supports SIZE.
STATUS:>         This site can resume broken downloads.
COMMAND:>         REST 0
                  350 Restarting at 0. Send STORE or RETRIEVE to initiate transfer
COMMAND:>         PASV
ERROR:>          Timeout (60000 ms) occurred on receiving server response.
ERROR:>          Failed to establish data socket.

Thanks in advance fellas,
Kirk

---

### Post by rickyjones on 2007-02-05
Try having the FTP user set their client to "PORT MODE" instead of "PASSIVE MODE" for the FTP transfer.

---

### Post by tturrisi on 2007-02-05
[http://kb.globalscape.com/article.aspx?id=10293&cNode=4K1J1P](http://kb.globalscape.com/article.aspx?id=10293&cNode=4K1J1P)
[http://forums.globalscape.com/tm.aspx?m=7900](http://forums.globalscape.com/tm.aspx?m=7900)

Try as stated above, use port mode.
And have 'em try to use commandline to connect and list files as a test.
Then have 'em test using a browser:
ftp:// username : password @ domain.com
(spaces addred to prevent forum  smilies)

---

### Post by cap10kirk on 2007-02-06
Thank you, fellas. Because of the info you posted, I was able to resolve my problems. This board rocks.:guitar: 

Kirk

---

### Post by tturrisi on 2007-02-06
so WHAT solutions did you used that resolved the issues?
(it's good to post them so that others can use the info)

---

### Post by cap10kirk on 2007-02-06
There were two billing companies. One simply used another FTP program, which worked. The other used the "port mode" for the transfer, which also worked.

Thanks again,
Kirk

---

