---
title: "Calendat server - DAViCalThunderbird setup"
date: 2010-03-12
forum: Server Platforms
---

### Post by kamaji792 on 2010-03-12
I apologise if this is an inappropriate place to put this information but as I could not find the information anywhere else I was keen it appear on the web somewhere.

I installed DAViCal using various sources of information onto a Hardy 8.04lts server.  All seemed fine until I came to connect Lightning (Calendar add-on for Thunderbird) to the remote calendar (I am sure the same applies to Sunbird the stand-alone calendar client).

The sticking point was the address you have to put in location of the calendar.  I could not find the correct address to enter.  In the end with a bit of detective work and trial and error (a lot of error) the following worked:

General
```
http://<server-name>/<cal-virtual-loc>/caldav.php/<user-name>/home
```
e.g.
```
http://192.168.0.2/cal/caldav.php/office/home
```

The full instructions are:
[LIST=1]
[*]Select a **New Calender...** (**File** > **New** > **Clender...**); Click **Next >**.
[*]Selcet **On the Netowork** radio button.
[*]Select **CalDAV** radio button; Set Location to:```
http://<server-name>/<cal-virtual-loc>/caldav.php/<user-name>/home
```Click **Next >**
[*]Set an appropriate **Name** for the calendar and **Color**; Click **Next >**.
[*]You should be asked for the calendar user name and password, so enter those.
[*]With any luck you should get a message "Your calender has been created; Click **Finish**.
[/LIST]

**Trouble shooting tip**

To check if the user name and password is correct. Type the following url into your browser:
```
http://<server-name>/<cal-virtual-loc>/index.php
```
You will then be asked for a user name and password.  If you can enter these correctly you will have access to the account details.

I have to repeat the installation process for another server.  I will try an log everything I do and get that documented.

For now atb

kamaji

---

