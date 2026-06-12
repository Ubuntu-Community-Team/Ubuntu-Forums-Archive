---
title: "diagnosis-helper: Our tool to help you help newbies better. [WE NEED YOUR HELP.]"
date: 2008-10-16
forum: Ubuntu Dev Link Forum
---

### Post by prototype_angel on 2008-10-16
Hi,

We've been working on an interesting project for the past week and is coming along nicely.

What is diagnosis helper?

A new user installing linux might run into several hardware issues and difficulties. Often, for the solutions, details about the modules, hardware, kernel, etc, etc have to be provided.

On message boards and email, it's painstaking to ask the user to execute one command after another often with large time zone delays.

Diagnosis helper aims to make this a better experience.

A user who needs help, runs this app, which has a GUI to choose what tests to run (ex. network, sound, etc), and all the pre-defined commands are run.

The output of those commands and files are written to a easily navigable html file, and can be uploaded or emailed or posted at forums. Now the people who want to help have a complete understanding of what the problem might be.

This application is written in python and pygtk. It is licensed under Apache License

You can see the project page here: [http://code.google.com/p/diagnosis-helper/](http://code.google.com/p/diagnosis-helper/)

---

### Post by prototype_angel on 2008-10-16
We need your help

We know a little bit about linux, but we need to know what kind of commands to run, so it will benifit the people who try to help other people.

So please suggest commands which might help diagnose a category of problems.
Examples
network

Execute

    * ifconfig
    * iwconfig
    * netstat 

Files:

    * /etc/network/interfaces 

graphics

Execute:

    * ? 

Files:

    * /etc/X11/xorg.conf 

etc,etc

Let the list be as exhaustive as possible Thanks!!

---

### Post by pavel989 on 2008-11-09
hardware:
dmesg and lsusb

im looking for the command (cant remember it) that checks if your ATI (radeon?) card has xgl or w/e. really helps whens etting up compiz.

---

### Post by alwayshere on 2008-11-09
sudo su

then

lshw

will give hardware info

---

