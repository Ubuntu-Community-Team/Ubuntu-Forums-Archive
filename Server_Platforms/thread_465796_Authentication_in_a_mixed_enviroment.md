---
title: "Authentication in a mixed enviroment"
date: 2007-06-06
forum: Server Platforms
---

### Post by alanandhispc on 2007-06-06
If you know that a new network design will incorporate a mixed environment of OS's (win & Linux), what is the best Ubuntu based authentication method?

I want to set something up from scratch and ensure that the same accounts can log on any machine, also i would like to ensure that logon scripts will run that will mount the appropriate remote drives in linux and the correct shares in windows - would this mean having a authentication system that see's if it's Linux to run a separate script in a separate fashion to windows?
The systems will all be fat clients.

The solutions i know exist for mixed environments are samba, samba with ldap & ldap (whilst using pgina with ldap for windows) - but what will work best in this scenario?



Regards,

Alan

---

### Post by craigp84 on 2007-06-06
Hi Alan,

With the exception of the obvious paid for solutions from Novel et al -

Your sticking point here is the XP client - it doesn't offer much in the way of authentication alternatives. If you want to stay sane, you'll put the XP clients in an AD domain GPOs really do make most tasks workable on windoze. Incidently, there's a common request for linux to support GPOs - it's a really misguided idea.

So that means on the linux clients, you're pretty much bound to using Kerberos, Winbind and some PAM magic to allow the users to authenticate & login.

Next up is home dirs. There's a choice to make in that, do you want the whole user's profile to be on the network and roamable (makes most sense normally) or just their my documents (saves space).

Either way, in windoze, you just setup an appropriate GPO and point it to your Windoze or Linux/Samba file server (you get some big wins by sticking this on a linux / samba share). You'll have to make decisions about folder redirection etc. it normally makes sense to do folder redirection on at least the mydocuments folder - which is good, because it makes sharing my docs with linux clients more reliable if it's always the current version of my docs on the server.

The alternative to folder redirection is forcing your users to logout of windows before they login to linux, this is because the my docs folder would only be copied back to the server at logoff (remember, sometimes this fails, plan accordingly).

Next up is making the linux clients work with this. Some people go down the route of seperate profile areas for linux and windoze, this is not always required.

Samba mount the home areas on /home from your file server. Set the "template homedir = /home/%U". The user's "home" on linux would be the %UserProfile% on linux.

You'll probably invest some time in creating a a skeleton home dir which is suitable for windoze and linux. Also, getting the Documents folder on a gnome desktop to point to My Documents is a pain. So it's easier to setup folder redirection for my docs on windoze to point to a "Documents" folder in the user's home / %UserProfile% folder.

This will mean shared firefox bookmarks & history across windows and linux (control your versions, deploy via GPO for ease on windoze), and a few other nicities.

-c

p.s. i enjoyed that, i must be really bored :-)

---

### Post by alanandhispc on 2007-06-06
That's a fantastic reply, thank you.


one thing would be how to ensure that no matter what os the user is in, they have a log on script to sort everything out. Now the AD side of things for windows is fine, but what about ubuntu? will the best way to be to have the pc setup to run a remote script regardless of who log's in, set within the Ubuntu skel account, or is there a more dynamic method?

I was thinking about not bothering with the home/my documents tie in, but that does seem a good way to do it. Main reason for that is most stuff is via mapped drives anyway, so i'd mount the same shares in Ubuntu.

i agree, marrying GPO's into Linux is not the way forward... it will be interesting to see what samba 4 has to offer when it arrives in the way of policy management.

Do you know of a way to have the skel account stored remotely? one way of doing the policy thing would be to have the skel account managed centrally and pulled down when there's changes..

Once again, thank you 

Alan

---

### Post by craigp84 on 2007-06-06
> will the best way to be to have the pc setup to run a remote script regardless of who log's in

You'd probably setup the /etc/profile to source /home/$USER/login.sh or similar (chown root and chmod 755 the script to prevent em changing it). Or have a generic login script for easier maintainance, which runs the above script if it exists - allows for the special cases, which always exist.

> I was thinking about not bothering with the home/my documents tie in, but that does seem a good way to do it. Main reason for that is most stuff is via mapped drives anyway, so i'd mount the same shares in Ubuntu.

Sounds a lot easier to maintain to me. Probably a much better option than all this faffing about.

> i agree, marrying GPO's into Linux is not the way forward... it will be interesting to see what samba 4 has to offer when it arrives in the way of policy management.

Where does samba come into policy management on a linux box? Same misguided reasoning i'm afraid!

> Do you know of a way to have the skel account stored remotely? one way of doing the policy thing would be to have the skel account managed centrally and pulled down when there's changes..

You'd probably make your own adduser script anyway, but the default one with ubuntu can be configured in /etc/adduser.conf. You'd set the location in here.

Hope it helps & let us know how you get on,

-c

---

### Post by alanandhispc on 2007-06-06
> i agree, marrying GPO's into Linux is not the way forward... it will be interesting to see what samba 4 has to offer when it arrives in the way of policy management.
Where does samba come into policy management on a linux box? Same misguided reasoning i'm afraid!

sorry i was talking about 2 different things there, i meant it's be interesting to see the supposed policy management that samba 4 will offer for windows clients, for the sake of having a non-ms authenitcation system in place that has policy management for windows clients.
I'm quite happy the way linux does things, they are seperate OS's after all, it's only the authentications and file access in the right places that need to be together, like it can be already, imo.

I didn't know you could point to different skel's through adduser, learn something new everyday.


Thanks

Alan

---

### Post by Chayak on 2007-06-06
I have similar requirements myself though I've yet to find a good solution.  I've been wondering if letting AD take care of the windows machines and setting up a Red Hat directory server for my linux machines and figuring out a way to replicate users between the two.  A common network storage is the easy part, it's getting a universal single sign on that's always been the issue.

---

### Post by craigp84 on 2007-06-06
> I've been wondering if letting AD take care of the windows machines and setting up a Red Hat directory server for my linux machines and figuring out a way to replicate users between the two

Yep, that's a workable approach too.

There's a lot of benefits around your suggested approach in terms of customisation, but for most folks that word just means "harder to learn, harder to use".

-c

---

