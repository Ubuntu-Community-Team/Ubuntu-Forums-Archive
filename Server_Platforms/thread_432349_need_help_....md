---
title: "need help ..."
date: 2007-05-03
forum: Server Platforms
---

### Post by hockey97 on 2007-05-03
Hi I want to be able to access my server over the internet, well I go to school during the day and take a class that I bought a computer for it's a eletronics class and we do have free time well friday's are our project day's and so  I want to access from that computer to my server I use webmin, I want to do this securely becuse the IT people for my school they take passwords and missuse them some people got their myspace accounts stolen becuse that student went on myspace and I know one IT guy used this to make money on the side with illegal advertising ect.

I want to hide myself from them like I want to hop to my server and my internet at home and not really use the school's, but I want to be able to not let them sniff my stuff when connected to my server. 

Is their any way that I could do this, I want to be hidden even the url ect becuse they would block it.

their like that.

My teacher said that he is ok with it but said that if the IT people or the principal has a problem with it then I am on my own.

would I have to have a proxy server?? or somthing?? 

Thanks for your time.

---

### Post by benanzo on 2007-05-04
you need something like a VPN. Webmin can do the VPN configuration if it's installed.  it will do SSL encryption of all your traffic.

[http://openvpn.net/](http://openvpn.net/)

openvpn is in the main ubuntu repos.

---

### Post by neouser99 on 2007-05-04
ok, without knowing to terribly much about networking you are diving in headfirst, but let's see if we can work something out.

first off, is all you want to do is browse the web like it's coming from  you computer and not the schools? the easiest way that you can do this i think is by using a tunnel through your server via a proxy (as you have indicated). walkthroughs/tutorials are always good, and in the spirit of DRY, [here]("http://lifehacker.com/software/ssh/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy-237227.php") is a good one.

-neo

---

### Post by hockey97 on 2007-05-04
I do know well about networking since I am taking a college course of eletronics we are covering netwroking ect I am going to take an A+ certification in  june. 

Well What I really want to do is work on my server at home from my school,  I will have the server on so I can access it over the net ,  however I need to do this hiddenly the IT people will get upset with me becuse

in our school policy they don't like proxy avoidance and so far their blocking so much stuff on the net.

So if do what you guy's suggested I want to really know that the IT people can't track it in any way.

I know they sniff the networks becuse one kid in my class went to federal prison for pirateing games and movies at school this is why I am kinda nervious doing this.

becuse I know they are really watching the networks now after that episode.

I just want to be able to access my server so I can update it install stuff using the web browser which hoping to use webmin but not just that I want to be able to like see the desktop on my screen at my school.

I  want something like remote host connection type thing, I have windows xo at school it's my computer I bought it but got a good price and no tax dues to  it'sa  lab fee.

and my server is ubuntu desktop thing, which I want to connect, but I don't want anyone at school including IT or administration to see my passwords or traffic.

and it would be nice if I could surf they internet using the internet from home for my computer at cpc.

but  the reason I want it hidden is becuse of the policy  It state's that if we use the schools internet we cannot use any program or tools to avoid proxy settings.

so kind in mind that it must be secure to the fullist otherwise I might get suspended.

Thanks for your time.

Thanks for the advice and responses.

---

### Post by hockey97 on 2007-05-08
How do you use that openvn thing???

when I am at school do I need to just type my external ip adress??

and at home do I need to forward the port ???

how to setup and use the tunnel securly.

and any tips on hideing the tunnel would be nice.

my school has a linux type system so would it be possible for them to

sniff my tunnel???

also that openvp thing need's to be installed on both the server and the client ect so that means I have to install it on my server and my computer at school???

I need somthing that at school I can use the  web browsers to get to my server or use the internet at home.

Thanks for your time.

---

### Post by hockey97 on 2007-05-09
HI my school has novell and want to know if their is any way to access my server from my school  my server is at home and I want to also be able to use my home's internet connection , I don't 
want to show any traces from my computer at school to my home for the IT people to see that I adoid their proxy server ect.

I downloaded a script that claims does this but don't fully know if it does I might try it tommaro at school.

how would I use the ssl protocal thing??

---

