---
title: "[SOLVED] GUI for SAMBA configuration?"
date: 2008-09-01
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-09-01
Can anyone recommend (apart from webmin) a GUI or webpage tool for configuring a SAMBA server?

I see mentions of SWAT and others but am just looking for recommendations. (preferrably something fairly easy to understand)

What I want is to configure folders with group access permissions on a workgroup file server. Not a domain controller or anything fancy.

I have tried and failed to configure SAMBA via the CLI.

I have my unix & samba users created and also unix groups but am failing at trying to understand how to create samba groups.

Thanks,

---

### Post by brad8266 on 2008-09-01
Whats wrong with using webmin? Its too easy to do with webmin. Using Webmin:

System >> Users and groups >>> Create a new group, I called mine "samba test"

Place the users that you want in the "samba test" group.

Go to Servers >> Samba >> now creat a new samba share, I called mine "Samba Test" 

Now go to Security and Acess COntrol for that share and add the group "samba test" to the valid groups section.

Done

EDIT- Nevermind I read in another thread you just want to get used to using CLI.

---

### Post by bab1 on 2008-09-01
> **G1ZmO65 said:**
> 
What I want is to configure folders with group access permissions on a workgroup file server.

I have my unix & samba users created and also unix groups but am failing at trying to understand how to create samba groups.



You can't create or manage groups with Samba.  In a nutshell Samba users are for authentication (who).  Unix users and groups are for authorization (you can use).

The best way to control users is the use of Access Control Lists (ACL).  ACL's are much more powerful and flexible than unix permissions.

Read very carefully --
 [http://ubuntuforums.org/showthread.php?t=480218]("http://ubuntuforums.org/showthread.php?t=480218") 

and --
 [http://tlug.dnho.net/?q=node/171]("http://tlug.dnho.net/?q=node/171")

---

### Post by G1ZmO65 on 2008-09-02
Thanks Bab1,

I'll certainly have a read through the links you suggested.

Yes, brad8266, my original intention was to configure samba wholy from the CLI for the sheer practice of doing so and I'd still like to do it that way if possible.
[COLOR="Red"][B]
Please consider this particular thread closed as I suppose webmin is the most commonly used GUI for configuring samba.[/B][/COLOR]

My other thread concerns samba via the CLI [here]("http://ubuntuforums.org/showthread.php?t=903408")

Thanks,

---

