---
title: "problem with call center program"
date: 2009-10-05
forum: Wine
---

### Post by eldersoares on 2009-10-05
HI!
i'm having a problem with the program teleprom, wich is used to call center solutions. this program has to connect to a server (smb) to display incoming calls.

when i press the button connect, i get run time error 430 "Class does not support automation or does not support expected interface". i've already installed mdac with winetricks because i read that it has something to do with it. but it didn't work. the terminal output is attached.

I GUESS the error has nothing to do with the connection process becase if i assign an inexistent server, it happens the same. i mean, i think there's something before, more related with graphics, buttons or glyphs, that is making it not to work. as far as i know, running under windows, in this exact moment appears a tray icon. 

THANKSSS!!!

---

### Post by eldersoares on 2009-10-05
well, things got a little better.
i installed dcom98 with winetricks and now the error doesn't appear anymore.
but the program still doesn't work as it should. i think it is at least connecting successfully with the server because if i try to connect to an inexistent IP, it shows a stranger behaviour.

the part that doesn't work is when the server tells the terminal there's an incoming call. it should appear a window in the terminal. it seems that the server can't communicate send this information. the server has win xp and the terminal , ubuntu 9.04.

i wonder if there's any problema with the pc's network name because in linux I can't connect to the server thru its network name only with the ip. otherwise, in the server (with win xp), there's no configuration that tells that it should connect with the terminal thru the ip or thru the name...

does anybody have any idea??
thanks

---

### Post by eldersoares on 2009-10-07
well well, so...
things seems to be working fine but, the main function of the system, show incoming calls, doesn't work. i've checked the connection between the client machine (ubuntu) and the server (win xp) and netstat command tells me the connection is established. if i run wine thru the terminal, there's no output in the moment that the server sends the information. is there anyway to see which information is being transported thru the ports??? would there be any other solution??

thanks again!!!

---

