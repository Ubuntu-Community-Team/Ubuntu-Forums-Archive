---
title: "Email server with push"
date: 2009-05-09
forum: Server Platforms
---

### Post by Toady00 on 2009-05-09
I've been running ubuntu on my laptop for about 3 months now and I love it. I still have quite a few windows boxes on my home network. I'm also running a windows home server. My question is I want an email server that supports "push" and windows mobile, and will let me store outlook calendars and contacts to be shared with all other clients on the network. Zimbra professional edition looks like it will do everything I need, but it requires a rather steep subscription price for the pro version. Is there any good free alternatives? Thanks for the help.

---

### Post by HermanAB on 2009-05-09
Howdy,

Citadel of course.  It has been around since about 1983 so you can be forgiven for never having heard of it...
;)

Here it is [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)
[http://aeronetworks.ca/citadel-basics.html](http://aeronetworks.ca/citadel-basics.html)

---

### Post by Toady00 on 2009-06-15
So I've got 9.04 server running with citadel on it. I've got the remote retrieval working for my emails from my isp's server. I can log in through WebCit and send and recieve my emails, and everything there seems to be working fine. My client is running XP SP3 and Outlook 2007 SP1. I've downloaded and installed Bynari's Insight Connector and followed all the instructions on their website (created a new profile like it said to do). Now comes the problem. If I create a new contact in the Global Address Book on outlook it doesn't show up in the Global Address Book Room in Citadel. If I create a new contact in Citadel's Global, I get a blank contact added in outlook. There is no information at all in the contact on outlook, but somehow if I search for the contact name it pulls up the blank contact and it looks like it has some kind of header with the contacts name but that is it. my calendar doesn't sync between the two either. I haven't tried anything else. I thought I might need to install LDAP so I grabbed openLDAP (slapd from repo). I also installed phpLDAPadmin and can access it through my web browser no problems (though I have no idea what I'm looking at when I do login). I went back into Citadel and updated the directory information for the LDAP server, and restarted Citadel. I went into outlook->Tools->Account Settings->Address Book->New and added the ldap server. I still have no change in syncing information between Citadel and Outlook, and for some reason I keep getting a message in the Aide room telling me that Citadel was unable to connect to the ldap server.

Just for reference:
server domain name - carolina.rr.com
ldap server (installed on same computer) - ldap.carolina.rr.com

citadel setting for ldap:
host name of ldap server - ldap.carolina.rr.com
port of ldap server - 389
base DN - dc=ldap,dc=carolina,dc=rr,dc=com
bind DN - cn=mylogin,dc=ldap,dc=carolina,dc=rr,dc=com

I appreciate any help anyone can give me. This is my first mail server, and I don't understand a lot of this stuff. I'm sure I'll have more issues when I try to get Funambol up and running for mobile access. Thanks in advance.

---

