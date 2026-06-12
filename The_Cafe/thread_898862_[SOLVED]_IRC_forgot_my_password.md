---
title: "[SOLVED] IRC forgot my password"
date: 2008-08-23
forum: The Cafe
---

### Post by hermes0710 on 2008-08-23
Hi all,
  i try to connect to irc.ubuntu.com but i forgot my password. What can i do? I tried using the command "sendpass" but i got "You are not authorized to perfom this operation...

---

### Post by Cope57 on 2008-08-23
What is the recommended way to set up my IRC nickname?  Please follow these steps to set up your nick and configure your client. Check off each step to make sure it's been done:

   1. Select a permanent, master nickname. If the nickname you want is registered but has not been used for at least 60 days, just ask a staffer and we'll be happy to drop it for you.

      Please avoid using the name of a community project or trademarked entity, to avoid conflicts. Write down your password and be sure to keep the sheet of paper in a safe place.

   2. Register your IRC nick:

          /msg nickserv register <your-password> <your-email> 

   3. To keep your email address private, rather than displaying it publicly, mark it as hidden:

          /msg nickserv set hidemail on 

   4. It's useful to have an alternate nick grouped to your account. This will ensure that you have a way to get online as a registered user (keeping any cloak you may have) in case your nick becomes frozen (a "ghost"). Many clients will automatically add an underline to your nick at connect time if the nick you specify is unavailable so it is advised to group the underlined nick. For example, if your primary nick is foo:

          /nick foo_ 

      and then

          /msg nickserv group 

      This will document that both nicks are owned by the same person and will allow services to leave you identified if you switch from your primary nick to your alternate and vice-versa.

   5. If you're running an older version of xchat and you've requested a cloak, you may need to follow these instructions so that your client will properly identify to Nickserv before joining any channels. Recent versions of xchat appear to handle things just fine.

   6. Configure your client to identify itself to nickserv automatically whenever it connects to freenode so that it's less likely you'll connect to the network without being identified to nickserv. The easiest approach is to specify your nickserv password as a server password.

   7. If your client can automatically try an alternate nick, set it to use the alternate nick you just registered. In this way, you'll make it much less likely that you'll ever appear without your registration (or your cloak if you have one).



server: irc.freenode.net

channel: #ubuntu

---

### Post by hermes0710 on 2008-08-23
I managed to reclaim my password after contacting an operator. So i had it sent to my registered email. Thanx though

---

### Post by suffice on 2010-02-18
Hey I know this post may be a bit old, but i having the same problem with my password.  I'm still a little new to IRC, using irssi
.
how would i msg the operator? the first person in the #freenode list?

I know that it was registered just fine, but just need the password emailed to my registered email somehow.

---

### Post by andrew.46 on 2010-02-19
Hi suffice,

> **suffice said:**
> how would i msg the operator? the first person in the #freenode list?

Look for the nicks that have a plus sign next to them and then message away. Might not hurt to do a quick:

```
/whois <nick>
```

to see if the person has marked themselves away or not...

> I know that it was registered just fine, but just need the password emailed to my registered email somehow.

It would not hurt to have a quick look to make sure all of your account details are set correctly *before* asking:

```
/msg NICKSERV info
```

All the best,

Andrew

---

