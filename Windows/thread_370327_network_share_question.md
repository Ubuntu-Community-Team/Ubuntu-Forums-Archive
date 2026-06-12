---
title: "network share question"
date: 2007-02-25
forum: Windows
---

### Post by dbbolton on 2007-02-25
i have a desktop, **FAMILY**, and a laptop, **LENNOX**, both running Windows XP Home Edition connected to a DSL modem. on both computers, the following account exists
username: **daniel**
password: **123456**

i ran Network Setup Wizard on both computers; both are in workgroup BOLTON and File/Printer Sharing is turned on for both computers.

when i go to Network Places on computer **FAMILY**, the following folders are visible: **SharedDocs on LENNOX**, and **SharedDocs on FAMILY**. however, when i view Network Places on computer LENNOX, only the folder **SharedDocs on LENNOX** is visible.

so, i clicked on "Add a Network Place". for the network address, i entered **\\FAMILY\SharedDocs** .

next, a dialogue box appears requesting username and password. the user name field is greyed out, and has **FAMILY\Guest** entered as the user name. the password field is blank.  (note that the Guest account is disabled on both computers.) 

i left the password field blank, and clicked OK. the dialogue box disappeared for a moment but quickly reappeared as it was before.

the second time, i entered **guest** as the password. then, a dialogue box appeared saying "The folder you entered does not appear to be valid. Please choose another."

so, i tried to Map Network Drive, but the same dialogue box comes up. next, i tried the option "Connect using a different user name." i entered **daniel **and **123456 **respectively. this brings up another dialogue box with **daniel **entered as the username and the password field blank. i entered **123456 **as the password and clicked OK. the dialogue box disappeared, and then another came up with **FAMILY\Guest** entered in the greyed-out username field.

does anyone know what's going on ?

---

### Post by miseljt on 2007-02-25
Try mapping specifically to the shares. Right-click on My Computer and click Map Network Drive. Select the paritition you want to mount to and type in \\(Computername)\(Sharename) and Connect. You should be able to go to My Computer and access the share as a different partition.


Edit: Sorry, didn't read the rest of your post before i made mine. Look through the command prompt for a command called 'net use' you can also map driver through that.

---

### Post by dbbolton on 2007-02-25
i saw the "net use" thing in a forum somewhere else. it gave error 62 or 67, i cant remember. but i'll give it another try.

edit:
>  # net use z:\\FAMILY\SharedDocs
System error 67 has occurred.

The network name cannot be found> # net use z: \\family\shareddocs
The user name or password is invalid for \\family\shareddocs

To connect 'FAMILY\Guest' to family, press enter, or enter a new user name: daniel
Enter the password for family:
System error 1326 has occurred.

Logon failure: unknown user name or bad password.

> # net use z: \\family\shareddocs /user:FAMILY\daniel
The user name or password is invalid for \\family\shareddocs

Enter the password for 'FAMILY\daniel' to connect to 'family':
System error 1326 has occurred.

Logon failure: unknown user name or bad password.

---

### Post by dbbolton on 2007-02-25
here's a strange discovery: when i tried to change the Windows Firewall settings on FAMILY, it won't let me select the 'Off' radio button ! there could be some massive spyware problems in it, as it's quite old. 

however, the hard drive on LENNOX is fresh from the factory, so i doubt it has any of those types of problems.

---

### Post by dbbolton on 2007-02-26
anyone else have an idea ?

---

