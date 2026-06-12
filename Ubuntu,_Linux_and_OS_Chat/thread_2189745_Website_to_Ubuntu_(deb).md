---
title: "Website to Ubuntu (deb)"
date: 2013-11-23
forum: Ubuntu, Linux and OS Chat
---

### Post by thumbtak on 2013-11-23
I have a great idea for an ubuntu or deb package that I want to create. I am unsure how to do this.

I have a few websites. One of the website has a way to chat with users. I want to create an application that is like a messanger, where you login and see all the users. This application would be able to be minimized and when a message is received, it would popup with the message. The application would use the mobile chat version of the website. The mobile chat version of the website would make it look like it is a native application.

How would I go about making this application?

---

### Post by ian-weisser on 2013-11-23
What programming languages do you know?

---

### Post by kostkon on 2013-11-23
You can make a[ ubuntu web app]("http://developer.ubuntu.com/web/") for it.

---

### Post by thumbtak on 2013-11-23
> **ian-weisser said:**
> What programming languages do you know?

I am not much of a programer. It is simple to make the application if you think you could help. It would not be hard. Quick.

---

### Post by thumbtak on 2013-11-23
> **kostkon said:**
> You can make a[ ubuntu web app]("http://developer.ubuntu.com/web/") for it.

I want to make something like this but basically make it contatined into its own web browser that when minimized it goes to the task bar. Also when people send messages it beeps and blinks.

Something that is kind of like Pidgin, but it does not need all the menus. Just a few. Like close, minimize, maximize, and maybe disable sounds and notifications.

I know with Android you can do this easily on a website. You put the URL and the icon along with a few simple changes, then you save it as an APK.

---

### Post by ian-weisser on 2013-11-23
Merely super-simplifying (dumbing-down) Pidgin or Empathy?
Yeah, probably not difficult at all. libpurple and telepathy are both well documented.
For that matter, so is irissi. And others.

Don't plan on anybody doing this *for* you. It's your idea. You are the person excited about it.
We can give you advice, and point you in the right direction.

---

### Post by thumbtak on 2013-11-24
> **ian-weisser said:**
> Merely super-simplifying (dumbing-down) Pidgin or Empathy?
Yeah, probably not difficult at all. libpurple and telepathy are both well documented.
For that matter, so is irissi. And others.

Don't plan on anybody doing this *for* you. It's your idea. You are the person excited about it.
We can give you advice, and point you in the right direction.

I figured that you or anyone else would not, but thought I would ask. I have no clue where to begin. Could you give me a starting point? I never designed an application in Linux.

---

### Post by ian-weisser on 2013-11-24
First research and select the project you want to base from: Pidgin (libpurple) or Empathy (Gnome/telepathy)

---

### Post by 3rdalbum on 2013-11-24
Making a Unity Web App seems like a vastly easier way to go than rewriting everything from scratch. By adding a few commands to your web page it will be able to pop up notifications to your desktop or display the number of unread messages in the app's icon.

---

### Post by thumbtak on 2013-11-24
> **ian-weisser said:**
> First research and select the project you want to base from: Pidgin (libpurple) or Empathy (Gnome/telepathy)

Pidgin would work. That is one I like more.

---

### Post by thumbtak on 2013-11-24
> **3rdalbum said:**
> Making a Unity Web App seems like a vastly easier way to go than rewriting everything from scratch. By adding a few commands to your web page it will be able to pop up notifications to your desktop or display the number of unread messages in the app's icon.

How does a Unity web app work on Xubuntu when it uses XFCE? I want it not to be just for Ubuntu. I want it to be for more then just Ubuntu.

---

### Post by ian-weisser on 2013-11-24
> **thumbtak said:**
> How does a Unity web app work on Xubuntu when it uses XFCE? I want it not to be just for Ubuntu. I want it to be for more then just Ubuntu.

See [http://developer.ubuntu.com/web/tutorial/](http://developer.ubuntu.com/web/tutorial/) . It's Unity-centric, but has a lot of good information.
There is not really a "Unity" webapp. Webapps are applications. Good applications work with many desktop environments.
In Xubuntu, applications (including webapps) use the Applications menu, have indicators and controls as a Panel Plugin, and the user can add them to a toolbar shortcut if they wish.
In Unity, applications (including webapps) show up in Dash, have indicators and controls in the appropriate AppIndicator on the top bar, and the user can add them to the Launcher Bar is they wish.

---

