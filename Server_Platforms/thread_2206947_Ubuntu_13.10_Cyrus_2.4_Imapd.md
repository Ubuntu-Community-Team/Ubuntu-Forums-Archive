---
title: "Ubuntu 13.10 Cyrus 2.4 Imapd"
date: 2014-02-21
forum: Server Platforms
---

### Post by Roswebnet on 2014-02-21
[FONT=Calibri][SIZE=3][COLOR=#000000]Ubuntu 13.10 Cyrus 2.4 Imapd[/COLOR][/SIZE][/FONT]
  [FONT=Calibri][SIZE=3][COLOR=#000000]Hi everyone,[/COLOR][/SIZE][/FONT]
  [FONT=Calibri][SIZE=3][COLOR=#000000]For a testing propose I installed an e-mail server on Ubuntu. It cost me couple of days to choose satisfied software and understand basic principles.[/COLOR][/SIZE][/FONT]
  [FONT=Calibri][SIZE=3][COLOR=#000000]I had in mind next requirements:[/COLOR][/SIZE][/FONT]
  [COLOR=#000000][FONT=Symbol][SIZE=3]·[/SIZE]         [/FONT][FONT=Calibri][SIZE=3]The software have to come from recent Ubuntu repository (tested, easy to install/remove).[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Symbol][SIZE=3]·[/SIZE]         [/FONT][FONT=Calibri][SIZE=3]Easy to configure and administer.[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Symbol][SIZE=3]·[/SIZE]         [/FONT][FONT=Calibri][SIZE=3]Good and clear documentation.[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Symbol][SIZE=3]·[/SIZE]         [/FONT][FONT=Calibri][SIZE=3]Good or great performance.[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Symbol][SIZE=3]·[/SIZE]         [/FONT][FONT=Calibri][SIZE=3]Good or great Security.[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Symbol][SIZE=3]·[/SIZE]         [/FONT][FONT=Calibri][SIZE=3]Future implementation of the exchange (MAPI). [/SIZE][/FONT][/COLOR]
  [FONT=Calibri][SIZE=3][COLOR=#000000]After some research, mostly a sogo documentation I found some packets which in most cases satisfy my requirements:[/COLOR][/SIZE][/FONT]
  [COLOR=#000000][FONT=Symbol][SIZE=3]·[/SIZE]         [/FONT][FONT=Calibri][SIZE=3]Postfix 2.10.2 as MTA[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Symbol][SIZE=3]·[/SIZE]         [/FONT][FONT=Calibri][SIZE=3]Cyrus 2.4.16 as MDA[/SIZE][/FONT][/COLOR]
  [FONT=Calibri][COLOR=#000000][SIZE=3]Choice of Postfix as MTA was quite easy, after reading two Wikipedia articles about most popular (so best documented) Postfix and Exim:[/SIZE][/COLOR][/FONT]
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]http://en.wikipedia.org/wiki/Postfix_(software)#Performance[/COLOR][/SIZE][/FONT]]("http://en.wikipedia.org/wiki/Postfix_(software)#Performance")
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]http://en.wikipedia.org/wiki/Exim#Performance[/COLOR][/SIZE][/FONT]]("http://en.wikipedia.org/wiki/Exim#Performance")
  [FONT=Calibri][COLOR=#000000][SIZE=3]In addition, I like how it is easy to configure a Postfix server and looks like postfix is a bit secure than Exim:[/SIZE][/COLOR][/FONT]
  [FONT=Calibri][COLOR=#000000][SIZE=3]I wondered why Cyrus often would suggested as a better choice than Dovecot. Finally, I found a great analysis report, where Cyrus beats Dovecot:[/SIZE][/COLOR][/FONT]
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]http://www.delaat.net/rp/2012-2013/p54/report.pdf[/COLOR][/SIZE][/FONT]]("http://www.delaat.net/rp/2012-2013/p54/report.pdf")
  [FONT=Calibri][COLOR=#000000][SIZE=3]In my virtualboxed Ubuntu server 13.10 I configured SMTP (25), Submission (587), IMAP (143), IMAPS (993). IMAPs recently turned off. I followed those tutorials:[/SIZE][/COLOR][/FONT]
  [FONT=Calibri][COLOR=#000000][SIZE=3]Postfix (Amavis spamassasin clamav)[/SIZE][/COLOR][/FONT]
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]https://help.ubuntu.com/community/Postfix[/COLOR][/SIZE][/FONT]]("https://help.ubuntu.com/community/Postfix")
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]https://help.ubuntu.com/13.10/serverguide/postfix.html[/COLOR][/SIZE][/FONT]]("https://help.ubuntu.com/13.10/serverguide/postfix.html")
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]https://help.ubuntu.com/community/PostfixAmavisNew[/COLOR][/SIZE][/FONT]]("https://help.ubuntu.com/community/PostfixAmavisNew")
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]https://my.spamexperts.com/kb/40/MTA-examples-to-set-use-a-smarthost.html#heading_toc_j_4[/COLOR][/SIZE][/FONT]]("https://my.spamexperts.com/kb/40/MTA-examples-to-set-use-a-smarthost.html#heading_toc_j_4")
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailclients.html[/COLOR][/SIZE][/FONT]]("http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailclients.html")
  [FONT=Calibri][COLOR=#000000][SIZE=3]Cyrus[/SIZE][/COLOR][/FONT]
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]https://help.ubuntu.com/community/Cyrus[/COLOR][/SIZE][/FONT]]("https://help.ubuntu.com/community/Cyrus")
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]http://www.opengroupware.org/en/users/docs/snippets/Configurations/CyrusAutocreate.html[/COLOR][/SIZE][/FONT]]("http://www.opengroupware.org/en/users/docs/snippets/Configurations/CyrusAutocreate.html")
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]https://cyrusimap.org/docs/cyrus-imapd/2.4.16/man/imapd.conf.5.php[/COLOR][/SIZE][/FONT]]("https://cyrusimap.org/docs/cyrus-imapd/2.4.16/man/imapd.conf.5.php")
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]http://social.technet.microsoft.com/Forums/office/en-US/626345d6-fece-4ccc-9660-2d494c2d1a9e/outlook-2013-imap-server-folders-not-syncing?forum=outlook[/COLOR][/SIZE][/FONT]]("http://social.technet.microsoft.com/Forums/office/en-US/626345d6-fece-4ccc-9660-2d494c2d1a9e/outlook-2013-imap-server-folders-not-syncing?forum=outlook")
  
  [FONT=Calibri][COLOR=#000000][SIZE=3]However, I came across a problem. When I log in from Windows Live Mail Cyrus automatically create only Inbox folder and no xlist-* rfc 6154 special maps (SENT DRAFTS TRASH etc.). In older versions there was an autocreate patch:[/SIZE][/COLOR][/FONT]
  [[FONT=Calibri][SIZE=3][COLOR=#0563c1]http://code.uoa.gr/p/cyrus/autocreate/[/COLOR][/SIZE][/FONT]]("http://code.uoa.gr/p/cyrus/autocreate/")
  [FONT=Calibri][SIZE=3][COLOR=#000000]There is no patch for 2.4.+.[/COLOR][/SIZE][/FONT]
  [FONT=Calibri][SIZE=3][COLOR=#000000]Does someone know how to solve this problem?[/COLOR][/SIZE][/FONT]
  [FONT=Calibri][SIZE=3][COLOR=#000000]Please see my final configuration files in attachment.[/COLOR][/SIZE][/FONT]
  [FONT=Calibri][SIZE=3][COLOR=#000000]Thank you.[/COLOR][/SIZE][/FONT]
  [FONT=Calibri][SIZE=3][COLOR=#000000]P.S.: I purged Cyrus and installed Dovecot. It is working as I expect, but I prefer to use a Cyrus (reasons above).[/COLOR][/SIZE][/FONT]
  [FONT=Calibri][SIZE=3][COLOR=#000000][ATTACH]250549[/ATTACH][/COLOR][/SIZE][/FONT]

---

### Post by Roswebnet on 2014-02-23
Hi everyone,
 I solve the problem for cyrus 2.4 on Ubuntu 13.10.
 In postfix main.cf:
 ```
mailbox_transport = lmtp:unix:/var/run/cyrus/socket/lmtp
```
 In cyrus cyrus.conf:
```
 imap                     cmd="imapd -U 30" listen="imap" prefork=0 maxchild=100
  
 # reindex changed mailboxes (fulltext) approximately every other hour
 squatter_1         cmd="/usr/bin/nice -n 19 /usr/sbin/cyrus squatter -s" period=120
```
  
 in imapd.conf:
```
 altnamespace: yes
 autocreatequota: -1  #it can be a positive value.
 allowplaintext: yes
 sasl_mech_list: PLAIN
 sasl_pwcheck_method: saslauthd
 #end of file:
 xlist-drafts: Drafts
 xlist-archive: Archive
 xlist-sent: Sent Items
 xlist-trash: Deleted Items
 xlist-junk: Junk E-mail
 xlist-spam: Junk E-mail
  
```
 Looks like it is working well, and creates special folders. Hoop it will be useful for somebody.

---

