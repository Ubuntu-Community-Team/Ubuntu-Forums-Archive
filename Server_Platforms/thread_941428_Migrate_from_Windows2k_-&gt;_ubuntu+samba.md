---
title: "Migrate from Windows2k -&gt; ubuntu+samba"
date: 2008-10-08
forum: Server Platforms
---

### Post by LarsEriksson on 2008-10-08
Hello.
I am the tech guy on a company with about 20-25 employees who logs in to a windows 2000 domain server, and now im buying a new server that im going to install Ubuntu on and use Samba as domain server.

As i have understood it each domain server has its own unique ID (SID), and when a client(WindowsXP-machine) connects to a domain it is the SID that tells WindowsXP what local account(with desktop, my documents and so on) that should be used. Am i correct?

And if i install ubuntu and set up samba as domain server, and then try to log in with a WindowsXP-client, a new local account will be created on the local machine, and therefore that user cant reach his/hers old desktop, settings and whatever was connected to the "old" account.

What i want is that the migration from w2k -> ubuntu+samba will go unnoticed by all the users in the office, so i figure, the easiest way should be to spoof the "old" SID from the w2k machine, is there a way to do this?

Or does anyone have any other solution to this, any guides, howtos or whatever?
Ive searched a while but i cant seem to find anyone else(relly wierd) who has this dilemma.

---

### Post by erwall on 2008-10-08
> **LarsEriksson said:**
> Hello.
I am the tech guy on a company with about 20-25 employees who logs in to a windows 2000 domain server, and now im buying a new server that im going to install Ubuntu on and use Samba as domain server.

As i have understood it each domain server has its own unique ID (SID), and when a client(WindowsXP-machine) connects to a domain it is the SID that tells WindowsXP what local account(with desktop, my documents and so on) that should be used. Am i correct?

And if i install ubuntu and set up samba as domain server, and then try to log in with a WindowsXP-client, a new local account will be created on the local machine, and therefore that user cant reach his/hers old desktop, settings and whatever was connected to the "old" account.

What i want is that the migration from w2k -> ubuntu+samba will go unnoticed by all the users in the office, so i figure, the easiest way should be to spoof the "old" SID from the w2k machine, is there a way to do this?

Or does anyone have any other solution to this, any guides, howtos or whatever?
Ive searched a while but i cant seem to find anyone else(relly wierd) who has this dilemma.

I would think the best way to do it is create a new domain w/the ubuntu server and have the clients join the domain and log into it.  This will create a new profile on the client as you said.  Then you can copy the old profile to the new one in My Computer --> Properties --> Advanced --> User Profiles as a local administrator on the client.  I would think this would be a cleaner way of doing it rather than messing w/the SID's.

---

### Post by LarsEriksson on 2008-10-08
Oh, actually i didnt know you could do that :) I will set up a test enviroment and try that. If it works, you are a lifesaver :)


Just some small side questions.
I will use "normal" ubuntu 64-bit, the GUI-ver, not the server ver. i think atleast.
Is there any good GUI for controlling/configuring Samba, a standalone(application form) GUI, or a web GUI, that anyone can reccomend?
And do anyone know of a basic guide/howto for a Samba domain server installation on ubuntu?

---

### Post by erwall on 2008-10-08
> **LarsEriksson said:**
> Is there any good GUI for controlling/configuring Samba, a standalone(application form) GUI, or a web GUI, that anyone can reccomend?
And do anyone know of a basic guide/howto for a Samba domain server installation on ubuntu?

You could try webmin or swat.

---

