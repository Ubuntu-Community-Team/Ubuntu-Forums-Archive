---
title: "Only able to see Apache as localhost, why?"
date: 2007-01-09
forum: Server Platforms
---

### Post by cocotu on 2007-01-09
I'm inside a network, I installed Apache in a Xubuntu box, but I'm only able to view the default page by typing **127.0.0.1/apache2-default/** which is the localhost and I'm not able to view this server from any other computer on the network.  Prev. I installed a LAMP server and everything went fine.  Whenever I type the machine's IP I get:

The page cannot be displayed
There is a problem with the page you are trying to reach and it cannot be displayed.

Please try the following:

    * Click the Refresh button, or try again later.
    * Open the Web site home page, and then look for links to the information you want.
    * If you believe you should be able to view this directory or page, please contact the Web site administrator by using the e-mail address or phone number listed on the Web site home page. 

10060 - Connection timeout
Internet Security and Acceleration Server

Technical Information (for support personnel)

    * Background:
      The gateway could not receive a timely response from the Web site you are trying to access. This might indicate that the network is congested, or that the Web site is experiencing technical difficulties.

    * ISA Server: isagatewayiii.exchange.goodwillny.org
      Via:

      Time: 1/9/2007 4:10:27 PM GMT 

Thanks for your help..

---

### Post by Modernity on 2007-01-09
The address your are using is a loop back address. Make sure you go into Admin and check the network properties for the machine. When inside, there should be a pull down menu for this to change. ( Quick and dirty explaination) Let me know if this helps.

---

### Post by cocotu on 2007-01-09
I'm using Xubuntu. When I go to Applications>System>Networking I check the Ethernet connection and I have set up a static IP. When I go to the Hosts tab I see

IP Address                    Aliases
10.0.3.238                     XubuntuLab  [COLOR="Red"]This is the machine apache is[/COLOR]
ff00::00                         ip6-mcastprefix
fe00::00                        ip6-localnet
ff02::02                         ip6-allrouters
ff02::1                           ip6-allnodes
::1                                 ip6-localhost ip6-loopback
127.0.1.1                       localhost.localdomain localhost XubuntuLab
ff02::3                            ip6-allhosts

Also, when I sudo /etc/init.d/apache2 restart I get:

* Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 10.0.3.238 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 10.0.3.238 for ServerName

And

xrgm@XubuntuLab:/etc/apache2$ **sudo netstat -patu**
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 localhost:mysql *:* LISTEN 4749/mysqld
tcp 0 0 localhost:3402 *:* LISTEN 4167/hpiod
tcp 0 0 *:netbios-ssn *:* LISTEN 4858/smbd
tcp 0 0 localhost.localdoma:ipp *:* LISTEN 5588/cupsd
tcp 0 0 *:microsoft-ds *:* LISTEN 4858/smbd
tcp 0 1 XubuntuLab:2557 mojave.daemon.be:www SYN_SENT 4303/freshclam
tcp6 0 0 *:www *:* LISTEN 5486/apache2
tcp6 0 0 *:ssh *:* LISTEN 4876/sshd
udp 0 0 XubuntuLab:netbios-ns *:* 4856/nmbd
udp 0 0 *:netbios-ns *:* 4856/nmbd
udp 0 0 XubuntuLab:netbios-dgm *:* 4856/nmbd
udp 0 0 *:netbios-dgm *:* 4856/nmbd 

Thanks

---

### Post by cocotu on 2007-01-09
It was a **firewall blocking**!! I had Firestarter blocking HTTP port 80. Now is working fine!! Thanks for your help, this is the best linux forum!!

---

### Post by Modernity on 2007-01-09
Glad you got it figured it.

---

