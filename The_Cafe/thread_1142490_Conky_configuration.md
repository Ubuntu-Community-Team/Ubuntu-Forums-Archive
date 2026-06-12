---
title: "Conky configuration"
date: 2009-04-29
forum: The Cafe
---

### Post by MeanEYE on 2009-04-29
Hi,

Well I have a question to all those who are familiar to this little utility. I've just finished my config and then I realised that I can use ${downspeedf} and others only for one particular network interface.

The problem is, I have conky installed on my laptop which I drag around with me a lot. At work, am connected to eth0, at home through wlan0 and when traveling I use my cellphone so probably usb0.

I would like to avoid putting aditional elements on my screen. Any toughts on how this could be done without taking too much aditional resources or procesor time?

---

### Post by m_duck on 2009-04-29
You could use conky's *if_up* variable. Check out the [conky documentation](http://conky.sourceforge.net/variables.html). It checks to see if your eth0 is up and if it is displays eth0 info, if it isn't up, it checks wlan0 and so on. Something along the lines of this should probably be OK:```
${if_up eth0}${addr eth0}${else}${if_up wlan0}${addr wlan0}${else}${if_up usb0}${addr usb0}{else}No Connection.${endif}${endif}${endif}
```
That might not work but something similar should do what you want. Obviously, if the code above does work it is only showing the IP for each connection, change the ${addr conn} to whatever info you want displayed for each connection.

---

### Post by MeanEYE on 2009-04-29
> **m_duck said:**
> You could use conky's *if_up* variable. Check out the [conky documentation](http://conky.sourceforge.net/variables.html). It checks to see if your eth0 is up and if it is displays eth0 info, if it isn't up, it checks wlan0 and so on. Something along the lines of this should probably be OK:```
${if_up eth0}${addr eth0}${else}${if_up wlan0}${addr wlan0}${else}${if_up usb0}${addr usb0}{else}No Connection.${endif}${endif}${endif}
```
That might not work but something similar should do what you want. Obviously, if the code above does work it is only showing the IP for each connection, change the ${addr conn} to whatever info you want displayed for each connection.

Oh sorry, I should have mentioned that. I already tried with ${if_up}. But that command tests wheter interface if up or not, it doesnt test if interface is connected. 

Meaning, if I do ifconfig I'll see eth0 and wlan0 every time but that doesnt mean am connected to wireless network or lan.

Am looking for a way to monitor download and upload speed for all interfaces together. It would be perfect if ${downspeed} could be writen without parameters.

---

### Post by MeanEYE on 2009-04-29
Is there ability to write something like this:
```

Address: ${addr ${gw_iface}}

```
?

Edit:

I've found [here]("http://git.omp.am/?p=conky.git;a=commit;h=2c3d57d84143f6013dad7b57beac6d155ed859ae") that this could be writen like this:
```
$${addr ${gw_iface}}
```

---

### Post by m_duck on 2009-04-29
Hmm, shame. The only thing I can really think of now is to use an external network monitor app that can compile the data from two or three interfaces, then use an execi line with some greps and cuts to display the info in conky. I'm just trying to find a suitable network monitor - I found one which looked promising but seems not to exist...

---

### Post by billgoldberg on 2009-04-29
> **m_duck said:**
> Hmm, shame. The only thing I can really think of now is to use an external network monitor app that can compile the data from two or three interfaces, then use an execi line with some greps and cuts to display the info in conky. I'm just trying to find a suitable network monitor - I found one which looked promising but seems not to exist...

Well conky has support for scripts, so I guess you could whip something up.

---

### Post by MeanEYE on 2009-04-29
> **billgoldberg said:**
> Well conky has support for scripts, so I guess you could whip something up.

Yes, conky supports scripts and I could easly write some. But my main concern here is not to increase processor or memory usage. After all they said escaping should be possible... So I guess in next version we can expect that since in this one it's not working!

---

### Post by MeanEYE on 2009-05-25
> **HairyBollocks said:**
> Whats conky?

Conky is highly configurable lightweight system stats display program. Just google "conky" for some screenshots.

---

### Post by matrovius on 2009-05-31
hi 

I had the same problem, and on the net is not easy to find.
Here my .conkyrc
I use these config on me netbook acer one, 
I use ubuntu 9.4 NRE.

so I see 3 options:

[LIST]
[*]the config of my lan
[*]the config of my wlan
[*]'no network connection"
[/LIST]
with if_empty look you in the file arp or there is some connection info..
you can best see that with 
sudo mousepad /proc/net/arp

there you can also see the names of your device, who has connection.
usefull for the correct devicename.

gedit doesn't work in my case, strange.


here my code, i hope you enjoy it.

```
NETWORK   ${hr 2}

${if_empty ${exec cat /proc/net/arp | grep eth0}}${if_empty ${exec cat /proc/net/arp | grep wlan0}}No Network connection
${else}WLAN IP: ${addr wlan0} $alignr ${wireless_mode wlan0} and ${wireless_bitrate wlan0}
SSID: ${wireless_essid wlan0}  $alignr Range: ${wireless_link_qual_perc wlan0} % / ${wireless_link_qual_max wlan0} %
${wireless_link_bar 6,240 wlan0}
Down: ${downspeed wlan0} k/s ${alignr} Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 20,115 000000 ff0000} $alignr ${upspeedgraph wlan0 20,115 000000 00ff00} 
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}${endif}
${else}LAN IP: $alignr ${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 20,115 000000 ff0000} $alignr ${upspeedgraph eth0 20,115 000000 00ff00} 
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}
```

---

### Post by MeanEYE on 2009-06-01
> **matrovius said:**
> hi 

I had the same problem, and on the net is not easy to find.
Here my .conkyrc
I use these config on me netbook acer one, 
I use ubuntu 9.4 NRE.

so I see 3 options:

[LIST]
[*]the config of my lan
[*]the config of my wlan
[*]'no network connection"
[/LIST]
with if_empty look you in the file arp or there is some connection info..
you can best see that with 
sudo mousepad /proc/net/arp

there you can also see the names of your device, who has connection.
usefull for the correct devicename.

gedit doesn't work in my case, strange.


here my code, i hope you enjoy it.

```
NETWORK   ${hr 2}

${if_empty ${exec cat /proc/net/arp | grep eth0}}${if_empty ${exec cat /proc/net/arp | grep wlan0}}No Network connection
${else}WLAN IP: ${addr wlan0} $alignr ${wireless_mode wlan0} and ${wireless_bitrate wlan0}
SSID: ${wireless_essid wlan0}  $alignr Range: ${wireless_link_qual_perc wlan0} % / ${wireless_link_qual_max wlan0} %
${wireless_link_bar 6,240 wlan0}
Down: ${downspeed wlan0} k/s ${alignr} Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 20,115 000000 ff0000} $alignr ${upspeedgraph wlan0 20,115 000000 00ff00} 
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}${endif}
${else}LAN IP: $alignr ${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 20,115 000000 ff0000} $alignr ${upspeedgraph eth0 20,115 000000 00ff00} 
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}
```

Is your config functional? I mean... does it work since you are using recursive variables as well...

---

### Post by matrovius on 2009-06-01
> **MeanEYE said:**
> Is your config functional? I mean... does it work since you are using recursive variables as well...


yes it is functional.

here 3 printscreens of my netbook.
I use the conkyconfig on my netbook: 
Acer One A110
Ubuntu 9.4 Jaunty NRE, (but the classic mode)
Conky version 1.6.1

the full conky file: [link]("http://users.telenet.be/matrovius/.conkyrc")

with LAN
[[IMG]http://img22.imageshack.us/img22/4504/nelisnetbook.th.png[/IMG]]("http://img22.imageshack.us/img22/4504/nelisnetbook.png")

With wireless
[[IMG]http://img24.imageshack.us/img24/462/nelisnetbook2.th.png[/IMG]]("http://img24.imageshack.us/img24/462/nelisnetbook2.png")

without any internet connection
[[IMG]http://img195.imageshack.us/img195/8232/nelisnetbook3.th.png[/IMG]]("http://img195.imageshack.us/img195/8232/nelisnetbook3.png")

---

### Post by MeanEYE on 2009-06-02
> **matrovius said:**
> yes it is functional.

here 3 printscreens of my netbook.
I use the conkyconfig on my netbook: 
Acer One A110
Ubuntu 9.4 Jaunty NRE, (but the classic mode)
Conky version 1.6.1

the full conky file: [link]("http://users.telenet.be/matrovius/.conkyrc")

with LAN
[[IMG]http://img22.imageshack.us/img22/4504/nelisnetbook.th.png[/IMG]]("http://img22.imageshack.us/img22/4504/nelisnetbook.png")

With wireless
[[IMG]http://img24.imageshack.us/img24/462/nelisnetbook2.th.png[/IMG]]("http://img24.imageshack.us/img24/462/nelisnetbook2.png")

without any internet connection
[[IMG]http://img195.imageshack.us/img195/8232/nelisnetbook3.th.png[/IMG]]("http://img195.imageshack.us/img195/8232/nelisnetbook3.png")

Great, thanx... I'll give it a shot... :D

---

### Post by hellion0 on 2009-06-02
Try if_connected instead of if_up. Works on my laptops.

---

### Post by MeanEYE on 2009-06-02
> **hellion0 said:**
> Try if_connected instead of if_up. Works on my laptops.

if_connected is not in their documentation... :D how the hell did you find it :)

oh, and thanx a lot :)

Edit: I've tried if_connected and it does not work... I too have Conky version 1.6.1

---

