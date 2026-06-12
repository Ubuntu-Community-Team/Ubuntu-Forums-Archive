---
title: "How to hide specific users at startup?"
date: 2010-07-30
forum: Security
---

### Post by dillandriskell on 2010-07-30
I don't want to hide all the users at startup, I only want to hide one specific user. Reason being I have two accounts; each having different startup programs, but one is hardly used and I don't like the clutter both provide. I know this is possible, as there's an "other" option at start up, but I've yet to identify how this is implemented.

Unfortunately Googling this only provided answers for older versions of Ubuntu within the clutter of how to remove all the users. Any help on this would be very appreciated, and both GUI and terminal answers work for me.

For relevancy I'm using 10.4

---

### Post by cdenley on 2010-07-30
You can probably add the user here in /etc/gdm/gdm.schemas
```

    <schema>
      <key>greeter/Exclude</key>
      <signature>s</signature>
      <default>**[COLOR="Red"]hiddenuser,[/COLOR]**bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap</default>
    </schema>

```

---

### Post by dillandriskell on 2010-07-30
> **cdenley said:**
> You can probably add the user here in /etc/gdm/gdm.schemas
```

    <schema>
      <key>greeter/Exclude</key>
      <signature>s</signature>
      <default>**[COLOR=Red]hiddenuser,[/COLOR]**bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap</default>
    </schema>

```

Hmm, I tried that but I don't know if it worked, as I don't know what the password would be, unless I've missed it miserably in the code you provided. :S

---

### Post by cdenley on 2010-07-30
> **dillandriskell said:**
> Hmm, I tried that but I don't know if it worked, as I don't know what the password would be, unless I've missed it miserably in the code you provided. :S

Password? Did you edit the file and add the user to be hidden to the list? Did you reboot? Did the user you wish to hide appear in the login menu?

---

### Post by bodhi.zazen on 2010-07-30
The other potential method would be to change the users uid. By default GDM does not show users with UID less then I think 1,000, perhaps 500.

---

### Post by cdenley on 2010-07-30
> **bodhi.zazen said:**
> The other potential method would be to change the users uid. By default GDM does not show users with UID less then I think 1,000, perhaps 500.

You're right, I just tested it. Any users with UID<1000 or is on the exclude list I mentioned will not be shown in GDM. Keep in mind that if you change the UID, though, any filesystem permissions apply to a user's UID, so make sure you fix the user's home directory and its contents, or anything else they may own.

---

