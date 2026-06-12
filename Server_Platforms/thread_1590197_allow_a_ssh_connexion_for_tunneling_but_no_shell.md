---
title: "allow a ssh connexion for tunneling but no shell"
date: 2010-10-07
forum: Server Platforms
---

### Post by mansonthomas on 2010-10-07
Hi,

  I need to allow connection to some users on a servers with key authentication so that they can setup a tunnel to access a web application.
 But I don't wan't them to have a access to a shell.

  How can I do that?

Thanks,
Thomas.

---

### Post by CharlesA on 2010-10-07
Check comment 4 [here]("http://www.itefix.no/i2/node/11980").

---

### Post by mansonthomas on 2010-10-07
Thanks !

I wonder if a CTRL+C or CTRL+Z could allow the user to get the shell anyway... I'll try.

I paste the solution here for memo : 

> 
Frostregen 
                          
                                Joined: 30.11.2009        
                                 Posts:         
     
                                Just for reference: For me it works        
**                        Task: Do not allow shell access, only tunneling.**

 Created "/bin/no_shell" skript with following content:
 [PHP]#!/bin/sh
 read -p "PRESS ENTER TO TERMINATE CONNECTION" TOTO
 exit 
 [/PHP]Afterwards change the login shell to /bin/no_shell directly in  /etc/passwd file. Should work via "Activate a user" too. Beware of  unix-linebreaks when editing from windows.
 I use this to tunnel vnc through copsshd, both running on the same machine with vnc only listening to localhost.
       
            
   


---

### Post by CharlesA on 2010-10-07
If that is set for the users shell, it won't do anything.

Ctrl+C will close the connection and Ctrl+Z will do nothing.

Here's what I had to do:

[LIST=1]
[*]Create /bin/no_shell and give it execute permission
[*]sudo adduser user
[*]sudo usermod -s /bin/no_shell user
[*]Login as that user and hit enter to close the connection.
[/LIST]

---

### Post by mansonthomas on 2010-10-07
I' ve  tested, read command require a variable name to put the content of what the user type.

I've corrected what i Paste.

And actually, CTRL+Z do nothing but display CTRL+Z and CTRL+C stop 'read' and execute the next command which is 'exit'.

It seems a good solution !

---

### Post by CharlesA on 2010-10-07
In that case it doesn't need anything, since all it's doing is showing some text and then exiting.

---

