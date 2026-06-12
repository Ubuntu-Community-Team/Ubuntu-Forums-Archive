---
title: "Null Modem?"
date: 2006-12-28
forum: Server Platforms
---

### Post by thanatosmin on 2006-12-28
I've been trying to setup another way to logon to my headless server besides ethernet. I've been told this can be done using two modems (my laptop doesn't have a serial connector). Is this true? If so, where might I find documentation on how to do this? I figured it'd be called a null modem connection, but that seems to be the exclusive domain of serial cables.

---

### Post by amo-ej1 on 2006-12-28
A serial connection is used often as a recovery scheme for remote server. On a regular, pre edgy machine you'd have a file /etc/inittab and you'd add an agetty to the ttyS0 or ttyS1 and set the baudrate that would (re)spwan a login prompt on the serial port. But in edgy with the new upstart /etc/inittab migrated to /etc/event.d something

---

### Post by thanatosmin on 2006-12-28
Sorry if I was ambiguous, but is this possible using a modem? I don't have a serial connection on my laptop, so I'm just checking before I go out and buy a USB->serial converter.

---

