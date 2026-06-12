---
title: "What would you change in service-discovery-applet?"
date: 2010-11-24
forum: Ubuntu Dev Link Forum
---

### Post by karlwbloedorn on 2010-11-24
I've been working with another undergraduate on a rewrite (in C) of the package service-discovery-applet that is currently written in python. Its current progress can be described as "almost ready for initial release". It will be licensed with GPLv3.

There are a number of issues with the current applet:

The "No plugin to handle _xyz._tcp" error message for any service type that has no plugin created for it yet. This is the most useless and annoying thing the applet 
could do.

Most of the icons used for the menu are just a "?" on a globe when there are icon names standardized by freedesktop.org that fit most service types perfectly well.

Notifications are used too much and are annoying. Notifications should only be used when the program is already running and a new service is advertised on the network. Multiple services of the same type should be grouped into the same notification.

Bugs that haven't been fixed, [https://bugs.launchpad.net/ubuntu/+source/service-discovery-applet](https://bugs.launchpad.net/ubuntu/+source/service-discovery-applet)

What I want to know from the user base is:
1. Which zeroconf services ([http://www.dns-sd.org/ServiceTypes.html](http://www.dns-sd.org/ServiceTypes.html)) that aren't listed below do you use or would want to see in the panel applet. If you mention one, please mention what program should be used when a user clicks on a menu entry of the service type.
        
_libvirt._tcp       
_workstation._tcp   
_ssh._tcp        
_http._tcp
_smb._tcp         
_sftp-ssh._tcp    
_udisks-ssh._tcp   
_rfb._tcp            
_ipp._tcp            

2. What features not discussed do you want or don't want in the rewrite? 

3. Do you want to see services that gnome/ubuntu can't do anything useful with (such as Northrup Grumman/Mission Systems/ESL Data Flow Protocol)?

Looking forward to some responses. ;)

---

### Post by markdegroot on 2010-11-25
Is there any way to add custom services to the applet?

---

### Post by karlwbloedorn on 2010-11-25
Well as a developer its fairly easy (just add a few lines and a handler function,, but in order to let the user add custom ones there would have to be some way for the user to specify a program to run with certain arguments from the avahi data ( such as hostname). They would also have to pick a freedesktop icon. But its definately a good feature to add once a good method has been devised. It seems doable though.

Thanks for the input

---

