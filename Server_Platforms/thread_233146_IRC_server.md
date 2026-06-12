---
title: "IRC server"
date: 2006-08-09
forum: Server Platforms
---

### Post by Jebus on 2006-08-09
Hi All,
       I'm looking to setup an IRC server on my ubuntu server, does anyone have any suggestions as to what way I should go about this? as im having trouble finding documentation around. 

  Cheers :D

---

### Post by Dedmon on 2006-08-10
try using ircd-hybrid

to install type 'sudo apt-get install ircd-hybrid' in the terminal

once installed you can test the server using irssi by typing 'irssi' in terminal then once it's open type '/connect 127.0.0.1' in irssi this will log you onto your new IRC server :)

once logged on you will get a MOTD similar to the one below. follow the instructions on this or for more help goto [http://ircd-hybrid.com/](http://ircd-hybrid.com/)

There's also brief description of this at [https://help.ubuntu.com/community/IrcServer](https://help.ubuntu.com/community/IrcServer)

> 
        _,met$$$$$gg.       ircd-hybrid
     ,g$$$$$$$$$$$$$$$P.    -----------
   ,g$$P""       """Y$$.".  
  ,$$P'              `$$$.  If you are seeing this, you have
',$$P       ,ggs.     `$$b: installed the ircd-hybrid package and
`d$$'     ,$P"'   .    $$$  you are now connected to your new IRC
 $$P      d$'     ,    $$P  server -- congratulations.
 $$:      $$.   -    ,d$$'  
 $$;      Y$b._   _,d$P'    Since you have just installed the
 Y$$.    `.`"Y$$$$P"'       package, there are some things you
 `$$b      "-.__            should do before going any further:
  `Y$$b                     
   `Y$$.                    1. Edit /etc/ircd-hybrid/ircd.conf to
     `$$b.                  suit your needs.
       `Y$$b.               
         `"Y$b._            2. Edit /etc/ircd-hybrid/ircd.motd (this
            `""""           MOTD) to suit your needs. You are free
                            to use this Debian swirl under the
                            Debian Open Use Logo License :)

                            3. Restart the server using invoke-rc.d
                            ircd-hybrid restart.

                            -- Joshua Kwan <joshk@triplehelix.org>



---

### Post by Ticha on 2006-08-16
hmm... thats cool... but i can't find the install packet :-I

I ve done the same as u sad :(

Can someone help me?

---

### Post by Predius on 2006-08-16
Are you sure you have the universe repositories? That's where ircd-hybrid is. If not, you can add them using the following guide:

[https://help.ubuntu.com/ubuntu/serverguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/serverguide/C/extra-repositories.html)

---

### Post by Klaidas on 2006-08-17
Also, you can use [bahamut]("http://bahamut.dal.net") :)

---

### Post by Kurt` on 2006-08-17
I personally prefer [ircu](http://coder-com.undernet.org/).

# sudo apt-get install ircd-ircu

---

### Post by soilets on 2008-05-15
> **Dedmon said:**
> try using ircd-hybrid

to install type 'sudo apt-get install ircd-hybrid' in the terminal

once installed you can test the server using irssi by typing 'irssi' in terminal then once it's open type '/connect 127.0.0.1' in irssi this will log you onto your new IRC server :)

once logged on you will get a MOTD similar to the one below. follow the instructions on this or for more help goto [http://ircd-hybrid.com/](http://ircd-hybrid.com/)

There's also brief description of this at [https://help.ubuntu.com/community/IrcServer](https://help.ubuntu.com/community/IrcServer)
ERROR: 

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by vandorjw on 2008-06-17
Does this work for Ubuntu Desktop Edition?

I guess I am going to find out.
Sudo apt-get install "file name"

If you're wondering why I want a IRC Server, well I need it for hosting an online game.

I don't need a client, Already got one. :)
> sudo apt-get install ircd-ircu

This worked, I saw it start the deamon,
How do I configure it?

---

### Post by vandorjw on 2008-06-23
bump

---

### Post by Standy on 2008-06-25
[http://azio.org/2007/05/01/howto-configure-yourself-a-nice-private-ircd-irc-server/]("http://azio.org/2007/05/01/howto-configure-yourself-a-nice-private-ircd-irc-server/")

i guess this should do the trix... ;)

---

