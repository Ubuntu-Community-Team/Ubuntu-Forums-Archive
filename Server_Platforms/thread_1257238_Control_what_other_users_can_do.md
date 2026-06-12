---
title: "Control what other users can do?"
date: 2009-09-03
forum: Server Platforms
---

### Post by danielgroves on 2009-09-03
Hi,

Is there a way to limit what other users can do and write all of their actions to a log file?  For example I wan to be able to stop people who can connect via SSH being able to access any other local machines like the router through a text based browser like w3m.  

Any support greatly appreciated.  
Dan.

---

### Post by juancarlospaco on 2009-09-05
Permissions and Groups. 
Dont let the users got sudoers privilege.

create very limited group and include all users there,
or do it one by one.
just like the "Guest" session on the desktop...

---

### Post by danielgroves on 2009-09-05
Thanks for your response.  How would I go about creating a new group, and how would a specify what the members of the group can do?

---

### Post by hessiess on 2009-09-05
When you create a new user a group is also created with the same name, users have to be in perticular groups to be able to do some things, you can add a user to a group with the usermod -g command.

The outher, potentilly more sccure option would be to use a chroot jail.

---

### Post by danielgroves on 2009-09-05
> **hessiess said:**
> 
The outher, potentilly more sccure option would be to use a chroot jail.


What is a chroot jail?  Why is it more secure?

---

### Post by hessiess on 2009-09-05
> **danielgroves said:**
> What is a chroot jail?  Why is it more secure?

A chroot creates a `fake' root filesystem, from inside which the only applications a user can use are those in the `fake' /bin and /usr/bin dirs. Which makes limiting what the user can do a simple matter of not installing any unneded applications inside the jail.

---

### Post by danielgroves on 2009-09-05
So, would a chroot jail or groups be easiest to maintain in the long run?  I guess a chroot jail would be the most secure, but I really don't think security is a huge issue.  I just need to stop certain programs being run by certain people.

---

### Post by hessiess on 2009-09-05
Groups would be easier to set up.

---

