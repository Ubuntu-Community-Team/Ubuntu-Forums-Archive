---
title: "Ubuntu desktop in ubuserver8.10"
date: 2008-11-07
forum: Server Platforms
---

### Post by Gipsy25 on 2008-11-07
Hey there ...i have a problem i am new to ubuntu and i unstalled ubu server 8.10 i would like to install the desktop (gui) but my problem is that i dont have access to the Internet ... (wireless only). 

I was wondering if it was a way to install it from cd. I did some research and i found i could add the cd (apt-cdrom add)  after it I tried : "apt-get install ubuntu-desktop" it says it cant find the package.

So i am stuck ... can you please help? 

Thank you.

---

### Post by RealPSL on 2008-11-07
Can you provide the output of ```
cat /etc/apt/sources.list
```

---

### Post by Gipsy25 on 2008-11-07
ok, thanks for the reply ... 
When i do cat /etc/apt/sources.list gives me a list that is very long ...
ALL the sentences have a "#" at the beginning of the sentence. 
Including the deb's
# Line commented out by installer because it failed to verify:
# deb-src http:// .....  
and continues like that all the wayt down.

Thank you.

---

### Post by RealPSL on 2008-11-07
This can get you a clean look at your sources.list ```
cat /etc/apt/sources.list | grep -v "^#"
```. I am just trying to make sure that the cdrom is referenced in the file.

---

### Post by lykwydchykyn on 2008-11-07
What kind of wireless is it?  Maybe it'd be easier to get that working first.

---

### Post by Gipsy25 on 2008-11-08
ok i tried what was suggested 

cat /etc/apt/sources.list | grep -v "^#"

but still no luck It says there is not package available on E

I understand E is the cd rom but i am not sure ...
So here i am still trying to use the cd to install the gui
I also tried the other cd (8.10 desktop version the one you can boot from) but it didn't work either ...

Just for the record i used
sudo apt-get install ubuntu-desktop and it comes back with ...

reading package list ... done
building dependency ...
reading state information
E:could not find the package ubuntu-desktop 

So i dont know if i am doing wrong or what ... now as far as the wireless card when i do lspci it says 

RaLink RT2561/RT61 802.11g pci
i actually have a trednet 108mbps 802.11g 
So this is what i have and what is going on ... Sorry i took me longer to respond but i had to go to work ... 

Thanks in advance

---

### Post by lykwydchykyn on 2008-11-08
Have you tried connecting the wireless?  Or do you need help with those commands?

---

### Post by Gipsy25 on 2008-11-08
Hey well thank you again for all the help ... i went to work and when i came back frustrated for the situation i installed the ubuntu desktop instead ...  (Yeah i know ... lazy ... but i wanted to try ...something new ... maybe i am not ready for the server version yet ... though i want to thank you for the help ... )
I am very new at this is seems to me that everything is more complicated than windows ... nothing seems to be plug and play, i cant find the control panel (dont know if there is one ...) its more complicated but i will try to  learn first before i even switch back .... 

Thanks again ... i will probably post more question in the future .... Any books i can get or reference to start on this that you might recommend ????

Regards ...

PS: how do i close the thread ??? i noticed that some people close them but dont know how ... 
:guitar:

---

