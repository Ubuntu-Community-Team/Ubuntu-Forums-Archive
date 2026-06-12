---
title: "Create Samba File Share to Windows Domain Clients?"
date: 2010-04-28
forum: Server Platforms
---

### Post by Lucky. on 2010-04-28
I feel ashamed for even asking this, since it seems like there's about 3 samba questions here every day.  However after an hour of searching, I keep finding strange variants that aren't what I need.

My Goal:  Create a single file share on an Ubuntu Server - share it via samba to Windows clients that are on a domain with active directory.  It sure would be nice if AD authentication would work - so users don't have to type in a linux user/passsword each time they want to access the share.

In my adventures, I've found the following items (which may overlap)

1.  Joining the server to a Windows Domain
2.  Turning the server into a Windows Domain Controller
3.  Authentication with LDAP (still not quite sure how/what this would do)
4.  Stuff with Kerberos
5.  Lots of people bickering about Samba 3/4 & how it's impossible to make Samba a PDC.

I'm not sure if I need to make the ubuntu server a domain controller or not...all I want to do is create a file share and share it on the domain...I don't need to make the ubuntu server a domain controller for that, right?  Maybe just a member?  Maybe nothing at all?

I guess if I want to authenticate stuff correctly (or forward authentication requests?  Not sure), I probably need to join the ubuntu server to the domain...I think.

But let's say I do join it to the domain...then how to I create a file share that is authenticated via active directory rather than a local ubuntu server account?  I see a dozen guides on joining the server to the domain, but nobody ever mentions sharing the folder over the domain.

The lines are also blurred between joining Ubuntu to the domain and making it a domain controller.  What should I keep an eye out to avoid in these tutorials?

Sorry to be so vague - I've really been searching a lot, but I get lost between the Kerberos/LDAP/Samba/WinBind etc...and I have a feeling I don't need all of these for something this simple.  If people know of a good tutorial for these, I'd appreciate it.  Tried the Samba HowTo, tried searching this forum, tried Google, etc.

---

### Post by snpz on 2010-04-28
First of all - i guess you dont have to make your Ubuntu server as domain controller.
You have to join your domain ([http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html](http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html)).
After joining domain, configure samba to share folders you need using permissions and usernames that are given by your windows domain controller.
I created structure pretty similar, but domain functions are not served by MS AD:
- Ubuntu domain controller using Ubuntu server 8.04, samba 3.0.28a + LDAP;
- File server with all user and department shares (Ubuntu server 8.04 + samba 3.0.28a) - server joined domain and is using all authorization tools provided by domain controller, so users using single-sign-on process can access all their information on local network, including e-mail (Zimbra)!

---

