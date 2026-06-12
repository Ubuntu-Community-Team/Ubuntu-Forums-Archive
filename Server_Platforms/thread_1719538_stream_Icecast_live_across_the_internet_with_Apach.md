---
title: "stream Icecast live across the internet with Apache2 Installed"
date: 2011-04-01
forum: Server Platforms
---

### Post by crazups on 2011-04-01
Hello All!

Ok, I have finally broken down and made my first post on the forum.  I took pride in reading posts from others and learning from their mistakes, questions, suggestions and resolutions to simply figure it out my previous problems on my own with time and effort.  Unfortunately this one has me stumped.

[B]
Here is what I would like to accomplish:[/B]

DJ and stream it live from my home (New Hampshire, USA) to my family (FLorida, USA) over/across the Internet via my own website that I currently host. I currently have a developed web page titled "Live" where I would like them to be able to navigate to, and to be able to listen to the stream from, but listening on windows media player is fine also.

[B]
Here is what I currently have:[/B]

-Apache2 up and running with no problems (on another computer running Ubuntu Server in the same house on the same home network)

-Icecast installed, configured and running (on the computer with Apache2 Server)

-IDJC (Internet DJ Concole) up and running (on a computer separate from the Server, but on the same home network running Ubuntu 10.10)....I can listen to myself streaming while on my home network using media player on any of the many laptops and windows pc's in the home (3 laptops, 5 pcs) while connected to the home network via 192.168.....:8002/stream

-I've set up and established an account with [dyndns.com]("http://dyndns.com") which allows me to "host" my own website from my Apache2 Server....it has been verified and working down in Florida! (successfully configured port forwarding on Belkin router)

-IDJC is configured to use port 8002, because I had problems with port 8000

[B]
Here is what I've tried but had no luck resolving my problem:[/B]

-created a new virtualhost on port 80 with redirect to port 8002 (stream.mysite:8002)

<VirtualHost music.yourdomain.net:80>
Servername music.yourdomain.net
Redirect 301 / [http://music.yourdomain.net:8002/](http://music.yourdomain.net:8002/)
</VirtualHost>

-i've created a proxy with downgrade to html 1.0 for Icecast's purposes but didn't really know what to type in the address bar.  I tried over 10 different ways: [http://public_ip:80](http://public_ip:80), public_ip:8002; mysite.dyndns.org:8002; stream.mysite.dyndns.org....and so on

<VirtualHost *:80>
        ServerAdmin [email]stream@example.org[/email]
        ServerName stream.example.org

        SetEnv downgrade-1.0 1
        SetEnv force-response-1.0 1

        ProxyRequests Off

        ProxyPass / [http://localhost:8002/](http://localhost:8002/)
        ProxyPassReverse / [http://localhost:8002/](http://localhost:8002/)

        <Location />
                Order allow,deny
                Allow from all
        </Location>
</VirtualHost>

-in Icecast .xml file i've changed hostname to: localhost;192.168....; mydomain.dynsnd.org; server.mydomain; my public IP; none helped

Any ideas?  I could post my Icecast xml config if need, but already feeling like this is long winded.

Thanks in advance!!:D

---

