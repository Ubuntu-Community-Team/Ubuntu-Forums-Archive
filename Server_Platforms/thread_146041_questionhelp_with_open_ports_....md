---
title: "question/help with open ports ..."
date: 2006-03-17
forum: Server Platforms
---

### Post by kewlbert on 2006-03-17
Hi
  i've been using linux for a while but now i've started to tinker around ....
:cool: 

so .. 
<n00b alert>
Recently i read up a bit on nmap and netstat. And out of curiosity i ran nmap -O for my own ip address and  it reported back that few ports were open for ssh, telnet, ftp etc.

As i understand if i kill the underlying service then the port shd be released as well so i tried finding if i could find any process that could account for telnet and/or ftp but there was nothing in my 'ps -ef' listing...so my ques is whats happening here?? why do i see these ports open in nmap results?

Also there is absolutely nothing in my /etc/initd.conf  (pardon me if the name isnt exact but i made sure of the name when i was cheking)

... So i went to shields up website and had my machine scanned and i was so happy to see a 100% pass with no ports reported  (ftp/telnet included)...

  But that has surely left me confused. Why is nmap reporting those ports as open??

I then ran nmap for an ip which i was sure is v secure and predictably it came back with perfect all ports locked out report....

so is there anything i can do which will be take me one step higher (not showing any open port for example?)

Just want to say that its not a case of me being paranoid over nothing. I am just trying to learn things.... so any suggestions are appreciated and if there are any good linnks/references then pls post them as well

</n00b alert>

Thanks in Advance.

---

### Post by LordHunter317 on 2006-03-19
You need to be more specific on what you've done.  Stories are great and wonderful, but no one can tell you what you saw if we don't see what you did.  Commands you ran, output you got, etc.

---

### Post by imagine on 2006-03-19
Check the first section of the ouput of *netstat --listening --programs --numeric-ports* to find out which process listens on what port.

---

