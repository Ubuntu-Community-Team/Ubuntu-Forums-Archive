---
title: "Dorm print server hosted on dell mini 10"
date: 2014-04-08
forum: Server Platforms
---

### Post by achtyl on 2014-04-08
I know its late in the spring semester but im sick of walking to my printer and plugging in via usb to print. I have a Brother HL-22208DW printer and since our dorm wireless network is provided  by the school I cant get my printer on the network. I previously had a dummy network set up but it was a PIA to switch back and forth so I could print and get to the internet. I was in my networking lab and I got the briliant idea of making a print server on a dell mini 10. Since it has WIFI I can just connect to the school WPA2 Enterprise network and share the connection to my lynksys E800 running DD-WRT firmware and have my onw network? Then by making my own network I can use a wireless security supported by my printer and run a printserver on the Mini so I can print from my laptop with ease. I was able to get the server onto the network but not wirelessly. I went to the library and connected it through ethernet and was able to get it on get a light gui on it xfce4 and get network manager installed. Network manager wasnt running right, I ran pkill nm-applet and then nm-applet and got it running right but after running it in terminal i cannot close the terminal without the manager quiting with the terminal. I am also not able to see any wireless network connections. Is there something I need to install to get my WIFI working or is there a way to enable it?

---

### Post by achtyl on 2014-04-08
I have made some headway, I got the wireless card to work. In my rush to set the system up and thinking ahead of where I was I over thought the wifi driver. I installed the Brodcom driver and now I can see the networks and connected to the school network successfuly. Now to tackle the Sharing of the internet connection. I would like to take the connection to the internet form the WIFI and share it over my ethernet to my Lynksys E800

---

### Post by achtyl on 2014-04-08
While messing around with the settings of the wired connection I found the Share with other computers option, selected it and plugged the ethernet cable into the Lynksys ports for computers and tested the connection. Upon testing the connection I was not able to connect to the internet with my laptop. Out of curiosity plugged in to the internet port on the lynksys I didnt think it would work because I wasnt using a crossover cable but to my surprise it did. I now have a working connection and my own network. Now for the print server.

---

### Post by achtyl on 2014-04-08
I have reached as far as my knowledge will get me I dont knwo where to go. I have made print servers with Server 2008 but never ubuntu server. I went to localhost:631 on both the server and my laptop connected to the network. Just as a recap I have a Brother HL-2280DW printer. Im confused on getting the printer installed. ANY HELP WOULD BE APPRECIATED, i was hoping for help but didnt get any so far so anything would be great!

---

