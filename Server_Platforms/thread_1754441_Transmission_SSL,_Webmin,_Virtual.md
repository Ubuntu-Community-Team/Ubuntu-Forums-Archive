---
title: "Transmission SSL, Webmin, Virtual"
date: 2011-05-10
forum: Server Platforms
---

### Post by Thegmandrive on 2011-05-10
Alright folks, 
I installed transmission-daemon and have it running and working. 
The only problem is the web interface is [http://www.mywebsite.com:9091/transmission/web/](http://www.mywebsite.com:9091/transmission/web/)

I tried to use ssl protocol [https://www.mywebsite.com:9091/transmission/web/](https://www.mywebsite.com:9091/transmission/web/) and i get the following error. 

Secure Connection Failed
      
      
      
      
      
        
        
          An error occurred during a connection to [www.mywebsite.com:9091]("http://www.mywebsite.com:9091").

SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)


How can I get this to use my SSL cert?

I run ubuntu 10.04 LTS with virtualmin and webmin. I have a virtual website setup, and i want to use that cert... 

any ideas? im totally lost :)

---

### Post by Thegmandrive on 2011-05-10
anyone have some suggestions? or any ideas?

---

### Post by BkkBonanza on 2011-05-10
I believe you have to use a proxy front end for this. I'm not really a Transmission user but a quick google seems to point this way. If Transmission doesn't have options built in for SSL then a proxy would be the only way (well, other than using SSH, which is very easy and just as secure if you have openssh-server already running).

Here is a link to setting up a proxy front end for Transmission, 

[https://forum.transmissionbt.com/viewtopic.php?f=8&t=6133](https://forum.transmissionbt.com/viewtopic.php?f=8&t=6133)

---

### Post by Thegmandrive on 2011-05-12
Ill have to check that out, I was hoping there was a way to do this thorugh virtualmin. But Im having a hard time finding that information. I use a virtualmin, and have a virtual server, so I don't want to screw things up :)

---

### Post by Thegmandrive on 2011-05-12
oh, how would I use ssh through a web browser? or are are you talking about something like Stunnel?

---

### Post by BkkBonanza on 2011-05-13
SSH has a "dynamic" proxy mode which can give you a SOCKS 5 proxy. It's quite easy to use if you have the server up and going already.

Instead of a normal login connection you use a command (on your local system) like,

ssh -fND 8080 user@server

-f = run background, which causes it to start the proxy and return to you (so to stop the proxy you need to use the kill command and process id)
-N = don't run any program at server end
-D = socks proxy on port 8080 (you can use any open local port)

When this command returns a proxy has been started on port 8080 on your local system (check with ps and netstat commands). Any connection requests to that proxy port using socks protocol get forwarded to your server and processed there "as if originating on that system".

Since Firefox has native socks support you just need to set it's network options to use SOCKS5 proxy on port localhost:8080. Any web traffic now gets encrypted and sent thru a tunnel to your server where it goes out from there. This works for any program that can use SOCKS such as browsers, email clients, and most torrent clients too.

There is a handy quickproxy plugin for FF that makes it a single button click to toggle proxy mode on/off. I use that to avoid manually changing the network options all the time. There is also a gui interface to the ssh proxy and tunnel commands using gSTM in the repos.

I've actually run Deluge (torrent client) thru this type of proxy so that only a single encrypted connection goes from my system to my server and then hundreds of torrent connections go out from there. But that is a different usage than just accessing the browser interface securely. It worked great for me as my ISP connection limited connections to block torrents. This allowed relaying them out to my server where they could go wild.

This type of proxy is great for secure browsing when out at cafes etc. It's not ideal for a "semi-public" secure interface to a torrent client. It's fine for your own personal use managing your torrents remotely.

Keep in mind once FF is using the proxy all URLs are treated as if from your server so the address localhost means the server localhost and is likely the address you need for your torrent client. In that case make sure the FF network options aren't bypassing localhost for the proxy as I think it has that address excluded in the proxy options by default.

---

### Post by Thegmandrive on 2011-05-13
wow! thanks for all your help 

I added 
ProxyRequests Off
    <Proxy *>
        Order Allow,Deny
        Allow from all
    </Proxy>

    ProxyPass /transmission [http://localhost:9091/transmission](http://localhost:9091/transmission)
    ProxyPassReverse /transmission [http://localhost:9091/transmission](http://localhost:9091/transmission)

to my apache server config , and well, it Worked!! I am excited to try to SOCKS. Thanks again for your help.

---

### Post by Thegmandrive on 2011-05-17
> **BkkBonanza said:**
> I believe you have to use a proxy front end for this. I'm not really a Transmission user but a quick google seems to point this way. If Transmission doesn't have options built in for SSL then a proxy would be the only way (well, other than using SSH, which is very easy and just as secure if you have openssh-server already running).

Here is a link to setting up a proxy front end for Transmission, 

[https://forum.transmissionbt.com/viewtopic.php?f=8&t=6133](https://forum.transmissionbt.com/viewtopic.php?f=8&t=6133)


After I added this to my Apache Configuration, I thought it was pretty cool that I don't need to have port 9091 open to the web anymore. The web interface still works! I can only assume this is due to the proxy being set up to use Localhost :).

---

### Post by BkkBonanza on 2011-05-17
If Transmission is bound to the localhost interface it shouldn't be exposed to the external interface, so should only be visible to the local machine (including Apache proxy which would expose the ssl port on your real IP). I'm not sure of the setting options in Transmission but you would want to check it's not bound to your real IP or * but only to localhost.

---

### Post by Thegmandrive on 2011-05-18
> **BkkBonanza said:**
> If Transmission is bound to the localhost interface it shouldn't be exposed to the external interface, so should only be visible to the local machine (including Apache proxy which would expose the ssl port on your real IP). I'm not sure of the setting options in Transmission but you would want to check it's not bound to your real IP or * but only to localhost.


hmm so, I no longer have port 9091 open (as far as my router configuration) I don't think I Fully understand what your meaning.
Transmission config has some settings that i updated, 
I left the "rpc-port": 9091,but I updated the other function to be"proxy-port": 443,
I added the follwing lines to the /etc/apache2/sites-available/mywebsite.com.conf
<Proxy *>
Order Allow,Deny
Allow from all
</Proxy>

ProxyPass /transmission [http://localhost:9091/transmission](http://localhost:9091/transmission)
ProxyPassReverse /transmission [http://localhost:9091/transmission](http://localhost:9091/transmission)

this allows me to log into the web interface using the HTTPS protocol, but does not allow non secured (which is exactly what I wanted)

---

### Post by BkkBonanza on 2011-05-18
If you run the cmd **sudo netstat -lntp** it will list what programs have open ports and on what interfaces. For example, it will show that Transmission is listening on port 9091 on either: 0.0.0.0 or 127.0.0.1

Either case would work for you and as long as you don't forward port 9091 thru your router then it's not a problem visible from the internet. It may be that Transmission doesn't have a config setting to decide what interface to listen on - in which case you don't have a choice. But if it does allow setting the interface then the "better" option would be to have it listen on "localhost" (127.0.0.1) as that would mean that only your own machine can connect to the port (which is what Apache is doing anyway), and the port isn't open to external connections even if your router were to allow a connection thru.

With your router set to not forward it's unlikely anyone would be able to bypass your ssl connection to Transmission - it's more a matter of completeness and understanding that I brought it up. 

The point being that when a program listens on a port it is actually listening on specific interfaces on that port, eg. **lo**, **eth0**, **wlan0** or what have you. When it is bound to lo then it can only be connected to by your system as lo is by nature not associated with a hardware network device. In the netstat output 0.0.0.0 indicates "any/all" which means it will accept connections on any interface.

---

### Post by Thegmandrive on 2011-05-19
> **BkkBonanza said:**
> If you run the cmd **sudo netstat -lntp**  it will list what programs have open ports and on what interfaces. For  example, it will show that Transmission is listening on port 9091 on  either: 0.0.0.0 or 127.0.0.1

Either case would work for you and as long as you don't forward port  9091 thru your router then it's not a problem visible from the internet.  It may be that Transmission doesn't have a config setting to decide  what interface to listen on - in which case you don't have a choice. But  if it does allow setting the interface then the "better" option would  be to have it listen on "localhost" (127.0.0.1) as that would mean that  only your own machine can connect to the port (which is what Apache is  doing anyway), and the port isn't open to external connections even if  your router were to allow a connection thru.

With your router set to not forward it's unlikely anyone would be able  to bypass your ssl connection to Transmission - it's more a matter of  completeness and understanding that I brought it up. 

The point being that when a program listens on a port it is actually listening on specific interfaces on that port, eg. **lo**, **eth0**, **wlan0**  or what have you. When it is bound to lo then it can only be connected  to by your system as lo is by nature not associated with a hardware  network device. In the netstat output 0.0.0.0 indicates "any/all" which  means it will accept connections on any interface.

ahhh, that makes way more sense, yeah, my router "no longer" forwards port 9091
There are a few settings in transmission that I was able to change in order to be local host instead of 0.0.0.0, 
tcp        0      0 127.0.0.1:9091          0.0.0.0:*               LISTEN      18229/transmission-

Im  concerned about some other settings. this next setting matches my PEER  listening port in the transmission config, I can change it to bind to  127.0.0.1 but then I can't download anything :) currently it shows 
tcp        0      0 0.0.0.0:20600           0.0.0.0:*               LISTEN      18229/transmission-


and then this looks like its the IPV6? should I change this?
tcp6       0      0 :::20600                :::*                    LISTEN      18229/transmission-


Sorry, one last question, related to ports and security. 

This  is the full netstat -lntp (Im changing anything that actually shows my  ipaddress to 1.1.1.1)root@myusername:/home/username# netstat -lntp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      875/mysqld      
tcp        0      0 0.0.0.0:587               0.0.0.0:*               LISTEN      1565/master     
tcp        0      0 0.0.0.0:110               0.0.0.0:*               LISTEN      1644/dovecot    
tcp        0      0 0.0.0.0:143               0.0.0.0:*               LISTEN      1644/dovecot    
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN      1092/spamd.pid  
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1736/perl       
tcp        0      0 0.0.0.0:80                0.0.0.0:*               LISTEN      483/apache2     
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN      1565/master     
tcp        0      0 1.1.1.1:53               0.0.0.0:*               LISTEN      853/named       
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      853/named       
tcp        0      0 0.0.0.0:22               0.0.0.0:*               LISTEN      983/sshd        
tcp        0      0 0.0.0.0:20600           0.0.0.0:*               LISTEN      18229/transmission-
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      917/postgres    
tcp        0      0 127.0.0.1:11000         0.0.0.0:*               LISTEN      925/lookup-domain-d
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1565/master     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      853/named       
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      483/apache2     
tcp        0      0 0.0.0.0:20000           0.0.0.0:*               LISTEN      1732/perl       
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      1644/dovecot    
tcp        0      0 127.0.0.1:9091          0.0.0.0:*               LISTEN      18229/transmission-
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      1644/dovecot    
tcp6       0      0 :::139                  :::*                    LISTEN      711/smbd        
tcp6       0      0 :::21                   :::*                    LISTEN      1662/proftpd: (acce
tcp6       0      0 :::53                   :::*                    LISTEN      853/named       
tcp6       0      0 :::22                   :::*                    LISTEN      983/sshd        
tcp6       0      0 :::20600                :::*                    LISTEN      18229/transmission-
tcp6       0      0 ::1:5432                :::*                    LISTEN      917/postgres    
tcp6       0      0 ::1:953                 :::*                    LISTEN      853/named       
tcp6       0      0 :::445                  :::*                    LISTEN      711/smbd      


should  i try to change any of these? some I assume have to be open to the web  :), like my virtualmin port and such. interestingly I don't see that  listed.. 

Would it be a good idea to set up some sort of proxy  for webmin as well? currently i access webmin by going to  [https://mywebsite.com:10000](https://mywebsite.com:10000)

Thanks for your patience, and thanks  for helping me out. I have read some things about this stuff online..  but now that I'm doing it, I find I keep coming up with more and more  questions.

---

### Post by BkkBonanza on 2011-05-19
Your torrent peer port would need to be 0.0.0.0 for it to be useful. Setting it to 127.0.0.1 would be like not having it. I generally don't bother with the peer port myself but I know it can slow down the torrents initially. It's not critical as the torrent client can still get the connections needed without it. In my case because I'm behind a router in my building (that I don't control) I can't actually listen publicly anyway, and I still get good torrent speeds without the peer port.

In your list above I would guess that virtualmin is shown as "perl". I don't use it but I believe it's written in perl and I wouldn't be surprised to see the port is owned by perl. Webmin probably 10000 and VirtualMin 20000. I don't know of any need to use a proxy on either since they support https.

I don't see anything really wrong in your list but I would probably make sure the smbd ports aren't forwarded thru your router. I would just look at each one and ask if you need it to be public. If you do then that's fine but if not then a good principle is to only expose the minimum required.

---

### Post by Thegmandrive on 2011-05-19
Yeah, it looks like the default settings for Virtualmin, and Webmin, are forced HTTPS. 
[https://www.mywebsite.com:10000](https://www.mywebsite.com:10000) will work 
[http://www.mywebsite.com:10000](http://www.mywebsite.com:10000) does not work. 

as far as the Peer port goes, I don't have port 20600 open, and my torrents still download wicked fast, In fact I have to limit my download speed to about 1.4 mbps 

ill be checking on my  smbd ports tonight. 

Thanks [[COLOR=#d40000]**BkkBonanza**[/COLOR]]("http://ubuntuforums.org/member.php?u=550406"), I'm really starting to love Ubuntu!

---

