---
title: "securely setting up printers"
date: 2012-11-02
forum: Security
---

### Post by jsvidyad on 2012-11-02
Hello, 

   I have a question regarding which way is more secure for setting up printers. The two options I have are:
1) The administrative user(the person with sudo privileges) can set up the printer for all users. Other normal users are NOT allowed to set up printers.
2) An individual user(normal desktop user with NO administrative sudo privileges) can be allowed to set up printers by suitably editing his account privileges.

Which option do you think is more secure?

---

### Post by Ms. Daisy on 2012-11-02
Is this a network printer or is it directly plugged into the computer?

---

### Post by jsvidyad on 2012-11-03
They are all network printers.

---

### Post by 2F4U on 2012-11-03
This is the same topic Linus Torvalds was venting about a couple of month ago. The traditional and more secure way is to only let an account with administrative privileges do the setup, but often it is more convenient for the user if he/she can do it.

---

### Post by jsvidyad on 2012-11-03
Which option is more secure? I will go with the secure option.

---

### Post by HermanAB on 2012-11-03
Does it really matter?  I agree with Linus that users should be able to configure printers.

---

### Post by Ms. Daisy on 2012-11-03
> **jsvidyad said:**
> Which option is more secure? I will go with the secure option. You'll have to make that decision based on who's using your network. Do you have lots of "guests?" If so, then you probably don't want everyone to have access. Is it just your trusted family using the network? Then you can probably give them all access.

Do you have wifi on the network? Is it password protected WPA2? Is it "free wifi" & accessible by anyone? The answers to these questions will result in different security needs. 

Also consider whether everyone using the network would even know how to properly set up a printer. Would it make sense from a usability standpoint for the administrator (you) to set up the printers for everyone, then just allow the folks access to an already set-up printer? Why does everyone need to set up a printer in the first place? Remember the basic principle to always give least privileges necessary.

---

### Post by jsvidyad on 2012-11-04
Hello, 

  I think I was a bit ambiguous in my first post. The printers are in my department(I'm in an university). The printers have already been set up by the system admin here. What I want to do is to be able to configure my ubuntu desktop to use those printers. For that, I have two options. The first one is for me to use the admininstrative account(the one with sudo privileges) on my computer to connect to the printer and do the setup for printing to it and allow all users to print to that printer. The second option is to allow a normal desktop user(without sudo privileges) on my desktop the privilege of connecting to the printer and setting up things by himself so that he can print to that printer. Right now, my desktop is not set up for printing to the printers

   Which option is better from a security point of view? Do you think allowing a normal user the privilege of setting up things so that he can print to a printer can create a security loophole for my desktop system? This is what I meant when I was talking about granting a normal user the privilege of configuring the printer in my first post. I was talking about letting him add the printer to his account all by himself.

  I'm sorry if my earlier post made you think that I had to set up the printers. My bad!

---

### Post by Ms. Daisy on 2012-11-04
I guess I'm still not understanding you. On all my computers I configured the network printers once & then just clicked "print" from then on. Do you have to configure it to print every time you print? Or are you saying you use a different printer every time you connect?

Also, how many people use this computer? From a usability standpoint, you need to let all the users print. 

From a security standpoint, yes there can be problems with network all-in-one printers.  But if  you're on a network that has pwned printers, then who configures the printers is the least of your problems.  I guess this is my long-winded way of saying I don't see a huge security risk here. In my opinion the need for usability outweighs security in this instance.

If it were me, I would configure the printers for all the users from the super user account & be done with it. But if it's something that is ongoing then the users would have to be able to configure the printers.

---

### Post by jsvidyad on 2012-11-06
> I guess I'm still not understanding you. On all my computers I configured the network printers once & then just clicked "print" from then on. Do you have to configure it to print every time you print? Or are you saying you use a different printer every time you connect?

I too want to configure my desktop to use the network printers. They don't have to be configured before each printing. The configuration has to be done just once(whether it be for all users or on a per-user basis). My question is whether to have the printers configured by the admin user(the one with sudo privileges) and permit all users to use those printers(in effect the admin user configures the printers to be used by everyone) or to give other users(normal users without sudo privileges) the ability to connect and configure the network printers(I have to edit the privileges of their user accounts for that)? I 'd like to know which is more secure.

> From a security standpoint, yes there can be problems with network all-in-one printers. But if you're on a network that has pwned printers, then who configures the printers is the least of your problems. I guess this is my long-winded way of saying I don't see a huge security risk here. In my opinion the need for usability outweighs security in this instance.

Th printers have been set up by the system admin in my dept. and I guess they can be assumed to be secure. That's not the issue. The issue is what I raised in the earlier part of this post.

> If it were me, I would configure the printers for all the users from the super user account & be done with it. But if it's something that is ongoing then the users would have to be able to configure the printers.

Once the admin user configures the printers and checks the option to let other users use it, the printers will be available for all new users too. So, you would suggest that I just do it for everyone by using the super user account? Is there anything wrong from the security point of view for the other option?

---

### Post by Ms. Daisy on 2012-11-09
> My question is whether to have the printers configured by the admin  user(the one with sudo privileges) and permit all users to use those  printers(in effect the admin user configures the printers to be used by  everyone) or to give other users(normal users without sudo privileges)  the ability to connect and configure the network printers(I have to edit  the privileges of their user accounts for that)? I 'd like to know  which is more secure. I can't imagine how it would be more secure to edit the privileges of the other users. I would configure the printer for all the users & just give them access to use them but not configure them.

---

### Post by jsvidyad on 2012-11-10
Thank You for your help.

---

