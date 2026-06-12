---
title: "IpMailer 1.0"
date: 2010-01-31
forum: The Cafe
---

### Post by Clordio on 2010-01-31
<updated to include GPL licensing>

Hi everyone, I wasn't sure where to post this but I wanted to share it with someone so here it is! This is my first "productive" program (meaning it does more than say hello world or count fibonacci numbers).

It is a python script that checks your external ip every hour and emails you when it changes. This is something I have found I needed so I decided to buckle up and learn some python and bash and I think it turned out really well! Please check it out and give me some feedback. Also let me know any problems or errors you get.

And now, the readme.txt!

```
IpMailer 1.1
Copyright 2010 George Shank

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>


#####IpMailer#######
A Python script that takes advantage of *nix
commands to check your external ip address
every hour and email you when it changes!

Once you download and bunzip2 the folder
go ahead and 'cd' into the ipmailer 
directory and type:

./emailsetup.py

Type in the email you wish to recieve the
ip updates (be sure this address will 
receive emails from dynamic ip's, some 
will automatically send these to the 
spam folder like gmail. For gmail just 
go into the spam folder and unmark the
conversation as spam and you will now
receive ip updates in your inbox!)

Now while in the same directory type:

./ipmailer.py

This will display an exitcode (this is 
normal). Once the time and date is displayed
you should check your email (possibly spam
folder) and check to make sure it worked.

Known Bugs:

Email is sent twice (something funky with the for loop)

Exitcode always displayed even when no error is needed to display

1/31/10
George Shank

```

You can just leave the terminal up and running in a different work space or you can go into your startup applications menu and add the ipmailer.py to the list so that it runs in the background on every startup!

EDIT:
Oops forgot to mention this needs sendmail so if you do not have this be sure to 

```
sudo apt-get install sendmail
```

---

### Post by juancarlospaco on 2010-01-31
Nice,
* Whats the Licence? GPL? BSD? WTFPL?*

---

### Post by Clordio on 2010-01-31
I'd like to make it gpl but I have no idea to go about that :confused:

EDIT:
Updated to include GPL licensing

---

