---
title: "is there a way to see who is logged on?"
date: 2009-10-18
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-10-18
I hosting a webpage uysing ubuntu 9 desktop with LAMP installed

people log on and do stuff using php and mysql

There are times when I need to reboot, and I would like to know if anyone is logged on, so i can reboot when no one is logged on.

---

### Post by Bachstelze on 2009-10-18
```
users
```

---

### Post by rhythmiccycle on 2009-10-18
i tried the code and it does not show be who it logged on my website. 

maybe "logged on" is not the right term,

i want to know if there is a session running on my website. 

the "users" code i think is used for computer logged on to the server.

I want to know if anyone singed on using a web browser,

---

### Post by Bachstelze on 2009-10-18
Well then you have to implement that in your code, there is no direct way to do it.

---

### Post by Lars Noodén on 2009-10-19
> **rhythmiccycle said:**
> I hosting a webpage uysing ubuntu 9 desktop with LAMP installed

people log on and do stuff using php and mysql



That would depend on your software written in PHP and how it tries to simulate account activity.    

The short real-world answer is: you can't.  HTTP is inherently stateless.
Every time a visitor gets something from your web site (a web page, an image for that web page, etc) the are logged in and then logged back out again.  

Whatever the PHP program does to try to hide that is basically a kludge.  But it might have some method of calling the account logged off if there have been no new requests after some time period.

---

### Post by windependence on 2009-10-19
> **rhythmiccycle said:**
> I hosting a webpage uysing ubuntu 9 desktop with LAMP installed

people log on and do stuff using php and mysql

There are times when I need to reboot, and I would like to know if anyone is logged on, so i can reboot when no one is logged on.

This should be pretty easy. Try this:

```
tiburon# netstat -f inet
Active Internet connections
Proto Recv-Q Send-Q  Local Address          Foreign Address        (state)
tcp4       0      0  192.168.2.40.http      227.133.102.97.c.1099  TIME_WAIT
tcp4       0      0  192.168.2.40.http      67-60-155-2.cpe..1032  FIN_WAIT_2
tcp4       0      0  192.168.2.40.ssh       192.168.2.4.56771      ESTABLISHED
udp4       0      0  localhost.ntp          *.*                    
udp4       0      0  192.168.2.40.ntp       *.*                
```

You can see that I am logged on as 192.168.2.4, and the other IPs are of course users logged on to the web site. When you have no IPs logged on except yours, do your reboot.

-Tim

---

### Post by rhythmiccycle on 2009-10-20
> **windependence said:**
> This should be pretty easy. Try this:

```
tiburon# netstat -f inet
Active Internet connections
Proto Recv-Q Send-Q  Local Address          Foreign Address        (state)
tcp4       0      0  192.168.2.40.http      227.133.102.97.c.1099  TIME_WAIT
tcp4       0      0  192.168.2.40.http      67-60-155-2.cpe..1032  FIN_WAIT_2
tcp4       0      0  192.168.2.40.ssh       192.168.2.4.56771      ESTABLISHED
udp4       0      0  localhost.ntp          *.*                    
udp4       0      0  192.168.2.40.ntp       *.*                
```


this is what I get when I try that:

```

mike@mike-desktop:~$ netstat -f inet
netstat: invalid option -- 'f'
usage: netstat [-veenNcCF] [<Af>] -r         netstat {-V|--version|-h|--help}
       netstat [-vnNcaeol] [<Socket> ...]
       netstat { [-veenNac] -i | [-cnNe] -M | -s }

        -r, --route              display routing table
        -i, --interfaces         display interface table
        -g, --groups             display multicast group memberships
        -s, --statistics         display networking statistics (like SNMP)
        -M, --masquerade         display masqueraded connections

        -v, --verbose            be verbose
        -n, --numeric            don't resolve names
        --numeric-hosts          don't resolve host names
        --numeric-ports          don't resolve port names
        --numeric-users          don't resolve user names
        -N, --symbolic           resolve hardware names
        -e, --extend             display other/more information
        -p, --programs           display PID/Program name for sockets
        -c, --continuous         continuous listing

        -l, --listening          display listening server sockets
        -a, --all, --listening   display all sockets (default: connected)
        -o, --timers             display timers
        -F, --fib                display Forwarding Information Base (default)
        -C, --cache              display routing cache instead of FIB

  <Socket>={-t|--tcp} {-u|--udp} {-w|--raw} {-x|--unix} --ax25 --ipx --netrom
  <AF>=Use '-6|-4' or '-A <af>' or '--<af>'; default: inet
  List of possible address families (which support routing):
    inet (DARPA Internet) inet6 (IPv6) ax25 (AMPR AX.25) 
    netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP) 
    x25 (CCITT X.25) 


```


i tried alot of variations but I can't get a output like the one in your example.

Do I need to install something?

---

### Post by windependence on 2009-10-20
Sorry about that. I was on the FreeBSD box. This should work in Linux:

```
tigere:~ # netstat --inet
```

The output should look like this:

```
tigere:~ # netstat --inet
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 tigere.dominicansto:ssh 192.168.2.4:59820       ESTABLISHED 
```

-Tim

---

### Post by Lars Noodén on 2009-10-20
@ windependence  : netstat doesn't show who is 'logged in' to the php app. It will show which connections are open, but that has little do to with the php app.  And with http being stateless, the only option there is to use a timeout.  

An [open tcp connection](http://www.vs.inf.ethz.ch/edu/WS0102/VS/TCP-State-Diagram.html) means that the ip address in question recently requested a web page.  

shutting down apache '[gracefully](http://www.vs.inf.ethz.ch/edu/WS0102/VS/TCP-State-Diagram.html)' should automatically accomplish anything you can do based on netstat data.  A graceful shutdown means that the http transactions are allowed to complete and the connections close naturally.  

See: 
[http://httpd.apache.org/docs/2.2/stopping.html](http://httpd.apache.org/docs/2.2/stopping.html)

It looks like that option is missing from /etc/init.d/apache2, so you will have to do it yourself:

```
sudo apache2ctl graceful-stop
```

---

### Post by windependence on 2009-10-20
Well, I know what you're saying but it should still give him an idea of whether there are people using his connection at the time. Just a suggestion.

-Tim

---

### Post by rhythmiccycle on 2009-10-22
> **Lars Noodén said:**
> 

It looks like that option is missing from /etc/init.d/apache2, so you will have to do it yourself:

```
sudo apache2ctl graceful-stop
```

I tried reading the link, but it was a little over my head. I don't really understand what the code does.

in a nutshell, in my site, users fill out forms, and php stores the data in a mysql data base. My concern is that if someone is in the middle of filling out a form, and then I reboot. When the user tries to submit it wouldn't work, because the "username" stored in the session data will be no longer in the memory.

does  graceful-stop, wait for all seasons to end and then shut down apache? does it prevent new sessions from starting? 

------
> **windependence said:**
> Sorry about that. I was on the FreeBSD box. This should work in Linux:

```
tigere:~ # netstat --inet
```

The output should look like this:



I'm going to test out that code soon, i just need to call a friend to sign on from outside.

---

### Post by Lars Noodén on 2009-10-25
> **rhythmiccycle said:**
> 
does  graceful-stop, wait for all seasons to end and then shut down apache? does it prevent new sessions from starting? 



Yes, but only the http sessions.  During the times your visitors are not in the process of actually downloading or uploading from your server, the connection is considered closed.  So, they could be in the middle of filling out a form when you reboot.  If your php program is robust enough it should be able to resume the old session after restarting.

---

### Post by rhythmiccycle on 2009-10-25
> **Lars Noodén said:**
>  If your php program is robust enough it should be able to resume the old session after restarting.

do you have a link with more info about resuming  the old session after restarting. I don't know if my program is "robust," i doubt it.

---

### Post by Lars Noodén on 2009-10-26
> **rhythmiccycle said:**
> do you have a link with more info about resuming  the old session after restarting. I don't know if my program is "robust," i doubt it.

The place to look is in the documentation for the PHP software you installed where "people log on and do stuff using php and mysql" or in the documentation for the user-tracking hack it uses.  

What PHP-based package are you using?

Background: HTTP and HTTPS are for one-off document retrieval.  Long interactive, stateful sessions might be done better using a java applet or something in Qt or GTK+.   'logging in' via PHP web page (or any other web service) is a kludge.  As far as the web server is concerned and as far as the Internet is concerned, when the last byte of the [current screen](http://tools.ietf.org/html/rfc2616#section-8) is downloaded, both the HTTP and TCP sessions are closed / over / done / finished.  With that in mind, a web authentication is '[forever](http://tools.ietf.org/html/rfc2616#section-15.6)' or until the browser or the server is restarted.  The program you are using probably uses its own authentication.  

```

                              +---------+ ---------\      active OPEN
                              |  CLOSED |            \    -----------
                              +---------+<---------\   \   create TCB
                                |     ^              \   \  snd SYN
                   passive OPEN |     |   CLOSE        \   \
                   ------------ |     | ----------       \   \
                    create TCB  |     | delete TCB         \   \
                                V     |                      \   \
                              +---------+            CLOSE    |    \
                              |  LISTEN |          ---------- |     |
                              +---------+          delete TCB |     |
                   rcv SYN      |     |     SEND              |     |
                  -----------   |     |    -------            |     V
 +---------+      snd SYN,ACK  /       \   snd SYN          +---------+
 |         |<-----------------           ------------------>|         |
 |   SYN   |                    rcv SYN                     |   SYN   |
 |   RCVD  |<-----------------------------------------------|   SENT  |
 |         |                    snd ACK                     |         |
 |         |------------------           -------------------|         |
 +---------+   rcv ACK of SYN  \       /  rcv SYN,ACK       +---------+
   |           --------------   |     |   -----------
   |                  x         |     |     snd ACK
   |                            V     V
   |  CLOSE                   +---------+
   | -------                  |  ESTAB  |
   | snd FIN                  +---------+
   |                   CLOSE    |     |    rcv FIN
   V                  -------   |     |    -------
 +---------+          snd FIN  /       \   snd ACK          +---------+
 |  FIN    |<-----------------           ------------------>|  CLOSE  |
 | WAIT-1  |------------------                              |   WAIT  |
 +---------+          rcv FIN  \                            +---------+
   | rcv ACK of FIN   -------   |                            CLOSE  |
   | --------------   snd ACK   |                           ------- |
   V        x                   V                           snd FIN V
 +---------+                  +---------+                   +---------+
 |FINWAIT-2|                  | CLOSING |                   | LAST-ACK|
 +---------+                  +---------+                   +---------+
   |                rcv ACK of FIN |                 rcv ACK of FIN |
   |  rcv FIN       -------------- |    Timeout=2MSL -------------- |
   |  -------              x       V    ------------        x       V
    \ snd ACK                 +---------+delete TCB         +---------+
     ------------------------>|TIME WAIT|------------------>| CLOSED  |
                              +---------+                   +---------+

                      TCP Connection State Diagram
                               Figure 6.

From RFC 793
http://tools.ietf.org/html/rfc793#section-3.2

```

It's not good or bad, that's just how it is.

---

### Post by rhythmiccycle on 2009-10-28
> **Lars Noodén said:**
> The place to look is in the documentation for the PHP software you installed where "people log on and do stuff using php and mysql" or in the documentation for the user-tracking hack it uses.  

....
  The program you are using probably uses its own authentication.  




 

The only thing I installed is LAMP and phpMyadmin

phpMyadmin says:
> 
    * Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch
    * MySQL client version: 5.0.75
    * PHP extension: mysqli


to be honest the things you are telling me are going over my head, but I want to learn.

I'm writting my own php script, everything is from scratch.

usersnames and passwords are stored in a mysql database

when user logs in this is run

```

<?php



	// start buffering the output

ob_start();



	//Start session

	session_start();

	

	//Include database connection details

	require_once("admin/config.php");

	

	//Array to store validation errors

	$errmsg_arr = array();

	

	//Validation error flag

	$errflag = false;

	

	//Connect to mysql server

	$link = mysql_connect(DB_HOST, DB_USER, DB_PASSWORD);

	if(!$link) {

		die('Failed to connect to server: ' . mysql_error());

	}

	

	//Select database

	$db = mysql_select_db(DB_DATABASE);

	if(!$db) {

		die("Unable to select database");

	}

	

	//Function to sanitize values received from the form. Prevents SQL injection

	function clean($str) {

		$str = @trim($str);

		if(get_magic_quotes_gpc()) {

			$str = stripslashes($str);

		}

		return mysql_real_escape_string($str);

	}

	

	//Sanitize the POST values

	$login = clean($_POST['login']);

	$password = clean($_POST['password']);

	

	 

	//Input Validations

	if($login == '') {

		$errmsg_arr[] = 'Login ID missing';

		$errflag = true;

	}

	if($password == '') {

		$errmsg_arr[] = 'Password missing';

		$errflag = true;

	}

	

	//If there are input validations, redirect back to the login form

	if($errflag) {

		$_SESSION['ERRMSG_ARR'] = $errmsg_arr;

		session_write_close();

		header("location: index.php");

		exit();

	}

	

	//Create query

	$qry="SELECT * FROM `members_main` WHERE userName='$login' AND passwd='$password'";

	

	

	

	$result=mysql_query($qry);

	

	echo '<p>'.$qry.'</p>';

	

	

	//Check whether the query was successful or not

	if($result) {

		if(mysql_num_rows($result) == 1) {

			//Login Successful

			session_regenerate_id();

			$member = mysql_fetch_assoc($result);

			

			//echo $member['member_id'];

			//echo '<p>ddd</p>';print_r($member);

			

			

			$_SESSION['SESS_MEMBER_ID'] = $member['userName'];

			$_SESSION['SESS_FIRST_NAME'] = $member['firstName'];

			$_SESSION['SESS_LAST_NAME'] = $member['lastName'];

			$_SESSION['SESS_Class'] = $member['class'];

			session_write_close();

			

		//this set of if's sends the user to the correct homepage	

			if($_SESSION['SESS_Class']=='Alg1a'){

				header("location: Classes/Alg1a/home.php");

				exit();

			}elseif($_SESSION['SESS_Class']=='Alg1b'){

				header("location: Classes/Alg1b/home.php");

				exit();

			}elseif($_SESSION['SESS_Class']=='Alg2'){

				header("location: Classes/Alg2/home.php");

				exit();

			}elseif($_SESSION['SESS_Class']=='Geo'){

				header("location: Classes/Geo/home.php");

				exit();

			}elseif($_SESSION['SESS_Class']=='LivEnv'){

				header("location: Classes/LivEnv/home.php");

				exit();

			}elseif($_SESSION['SESS_Class']=='Admin'){

				header("location: ../admin/ToolBox.php");

				exit();

			}else{

				header("location: member-index.php");

				exit();

			}

		}else {

			//Login failed

			header("location: login-failed.php");

			exit();

		}

	}else {

		die("Query failed");

	}

/**/	

	// print the contents of the buffer

ob_end_flush();

?>


```

then at the top of everypage inlclude this code

```

<?php

	//Start session

	session_start();

	

	//Check whether the session variable SESS_MEMBER_ID is present or not

	if(!isset($_SESSION['SESS_MEMBER_ID']) || (trim($_SESSION['SESS_MEMBER_ID']) == '')) {

		header("location: ../access-denied.php");

		exit();

	}elseif($_SESSION['SESS_Class'] != 'Alg1a'){

		header("location: ../access-denied-wrongClass.php");

		exit();

	}

?>

```

---

### Post by rhythmiccycle on 2009-10-28
> **windependence said:**
> Sorry about that. I was on the FreeBSD box. This should work in Linux:

```
tigere:~ # netstat --inet
```


-Tim


can you help me make sense of this output.

I did the net stat 3 times.

first time, I was signed on my site, and connected to my server using remote desktop. this was the code:

```

$ netstat --inet
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 mike-desktop.loca:41062 channel18.01.05.sf2:www ESTABLISHED
tcp        0      0 mike-desktop.loca:41061 channel18.01.05.sf2:www ESTABLISHED
tcp        0      0 mike-desktop.loca:55466 209.18.38.170:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:41054 channel18.01.05.sf2:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:37219 24.143.194.75:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:44046 24.143.194.26:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:37220 24.143.194.75:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:57995 69.63.187.16:www        ESTABLISHED
tcp        0      0 mike-desktop.loca:55460 209.18.38.170:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:55463 209.18.38.170:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:55464 209.18.38.170:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:41053 channel18.01.05.sf2:www TIME_WAIT  


```

then I did it again,  I can tell by my logs that someone had recently submitted info to the database. this was the code:

```

$ netstat --inet
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 mike-desktop.loca:33962 ad4.rtm-1.vip.rm.ac:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:33963 ad4.rtm-1.vip.rm.ac:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:58863 mg2a.mail.vip.re1.y:www ESTABLISHED
tcp        0      0 mike-desktop.loca:54592 channel18.01.05.sf2:www ESTABLISHED
tcp        0      0 mike-desktop.loca:60356 channel18.01.05.sf2:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:58859 mg2a.mail.vip.re1.y:www ESTABLISHED
tcp        0      0 mike-desktop.loca:53394 rmts.ads.vip.ac2.ya:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:33945 ad4.rtm-1.vip.rm.ac:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:34042 24.143.194.74:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:54593 channel18.01.05.sf2:www ESTABLISHED
tcp        0      0 mike-desktop.loca:37973 www-12-01-snc2.face:www ESTABLISHED
tcp        0      0 mike-desktop.loca:33953 ad4.rtm-1.vip.rm.ac:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:37066 yo-in-f149.1e100.ne:www ESTABLISHED
tcp        0      0 mike-desktop.loca:57283 208.71.120.60:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:33952 ad4.rtm-1.vip.rm.ac:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:51815 24.143.194.57:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:34763 fam.data.vip.re4.ya:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:36300 yo-in-f148.1e100.ne:www ESTABLISHED
tcp        0      0 mike-desktop.loca:52940 cdn-208-111-128-6.l:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:36404 208.71.122.95:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:33944 ad4.rtm-1.vip.rm.ac:www TIME_WAIT  
tcp        0      0 mike-desktop.loca:50286 216.52.167.81:www       ESTABLISHED
tcp        0      0 mike-desktop.loca:40886 24.143.200.57:www       ESTABLISHED

```

and this one is really late at night, and I know no one is using the site

```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      1 mike-desktop.loca:50804 channel18.01.05.sf2:www SYN_SENT   
tcp        0      1 mike-desktop.loca:50806 channel18.01.05.sf2:www SYN_SENT   
tcp        0      1 mike-desktop.loca:50805 channel18.01.05.sf2:www SYN_SENT   
tcp        0      1 mike-desktop.loca:50802 channel18.01.05.sf2:www SYN_SENT   
tcp        0      0 mike-desktop.loca:56961 www-12-01-snc2.face:www ESTABLISHED

```


what does "SYN_SENT" "ESTABLISHED" "TIME_WAIT" mean?

if I don't see any "TIME_WAIT" does that mean all sessions are closed?

---

### Post by windependence on 2009-10-28
The three-way handshake required to establish a new TCP connection involves a SYN from the source, a SYN/ACK from the destination, and a final ACK from the source. SYN_SENT in netstat means the handshake isn't complete. Apparently, a connection was requested and never established from this machine. IOW, it never was connected so you can probably ignore it. The ESTABLISHED connections are the only ones that really matter for you, but remember even if a connection shows established, you don't know how long the user was or is connected, hence what Lars is talking about being stateless. This only gives you an IDEA of activity on the server, but you can be resonably sure if you are showing little or no established connections like you see at night, it's probably OK to reboot if you must. 

As Lars mentioned a good PHP script would be able to resume or save the session. I'm not a PHP guru, but there are plenty of resources on the web, and even in this case, google is your friend.

-Tim

---

### Post by Lars Noodén on 2009-10-28
> **rhythmiccycle said:**
> 
what does "SYN_SENT" "ESTABLISHED" "TIME_WAIT" mean?

if I don't see any "TIME_WAIT" does that mean all sessions are closed?
You can see more information about the TCP states in RFC 793
[http://tools.ietf.org/html/rfc793#section-3.2](http://tools.ietf.org/html/rfc793#section-3.2)

Also, look up OSI ([Open Systems Interconnection](http://www.erg.abdn.ac.uk/users/gorry/eg3561/intro-pages/osi.html)).  There is a 7 layer model and a simplified 5 layer model.  TCP/IP is the transport/network layer(s).  HTTP goes on top of that.  Your PHP app goes on top of that.  

However, TCP is not so relevant for your goals, HTTP is.  The best you can do is let the server do a graceful shut-down: disallowing new HTTP requests, allowing the outstanding HTTP requests to be completed, and then after all HTTP requests are completed, stop.

sudo sh -c "/usr/sbin/apache2ctl graceful-stop ||*/usr/sbin/apache2ctl stop"

Each HTTP connection is a one-off (we'll let the issue of keep-alive connections slide for now): request-response-finish.  

During setup:
1. Request
During tear-down:
1. Response

Inside that request-response-finish shot is your regular tcp 3-way handshake to start up, a 2-way data transfer (request and response) and the 4-way handshake to shut down.

During setup:
1. SYN
2. SYN/ACK
3. ACK

During tear down:
1. FIN
2. ACK
3. FIN
4. ACK 

So even if your visitor is working filling out a form, as far as HTTP is concerned he is done for the day.  When HTTP is done, you don't have to look deeper.  

<grumble target="google">The reference materials are darn hard to find in Google these days, I'm getting no English material AND only Non-Authoritative results despite searching for known RFCs ... </grumble>

If you want to write a stateful retrieval protocol, the time might be right.  How about Z39.50-lite?

---

### Post by rhythmiccycle on 2009-10-30
Thanks alot everyone for your help.

I need to take some time and look into all this stuff. I'm really busy so its going to take me a while.

you all gave me a lot of good info. now I need to just digest it all. 


thanks again.

when I have new questions I'll start a new thread.

---

