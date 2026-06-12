---
title: "help needed for smf forum"
date: 2011-11-04
forum: Server Platforms
---

### Post by fubar2010 on 2011-11-04
Ok looks like its my first post :)

Right im not a wizard at this stuff,but i will try and explain what is happening,i have installed ubuntu server on a pc i have and have it running on a home network,this works fine.

I have installed smf,because for the last few years i have been using free forums and i have now decided to make my own forum using smf,so i have purchased a domain name and a far as i was aware set up my smf forum,which works fine on my local network.

So i am using go daddy dns to connect my domain name to my external address,which works fine.

so now for the problem,if i connect everything works fine(i think it has something to do with internal ip or something),but for anyone else they can only see the first page,if they try and register or look through the forum as a guest(this will be locked once i find the problem),they get a cant connect error or something like that.

Ok well have a look for your self [www.world-gamerz.com]("http://www.world-gamerz.com")

Well if i give my friend my external ip,he can get in the forum and register or just look around.

so i am hoping someone here can help,is it something to do with go daddy,ubuntu or my router ? :confused:

Cheers for any help given

---

### Post by sffvba[e0rt on 2011-11-04
*Thread moved to **Server Platforms**.*


404

---

### Post by Fragadelic on 2011-11-04
> **fubar2010 said:**
> Ok looks like its my first post :)

Right im not a wizard at this stuff,but i will try and explain what is happening,i have installed ubuntu server on a pc i have and have it running on a home network,this works fine.

I have installed smf,because for the last few years i have been using free forums and i have now decided to make my own forum using smf,so i have purchased a domain name and a far as i was aware set up my smf forum,which works fine on my local network.

So i am using go daddy dns to connect my domain name to my external address,which works fine.

so now for the problem,if i connect everything works fine(i think it has something to do with internal ip or something),but for anyone else they can only see the first page,if they try and register or look through the forum as a guest(this will be locked once i find the problem),they get a cant connect error or something like that.

Ok well have a look for your self [www.world-gamerz.com]("http://www.world-gamerz.com")

Well if i give my friend my external ip,he can get in the forum and register or just look around.

so i am hoping someone here can help,is it something to do with go daddy,ubuntu or my router ? :confused:

Cheers for any help given

Your settings are wrong - you have your internal IP pointing to your forum:

```
Firefox can't establish a connection to the server at 192.168.1.100
```

That is a private IP and is not routeable over the internet.  You must have an external IP on the forum box and you hopefully already have some sort of firewall.

---

### Post by fubar2010 on 2011-11-04
> **Fragadelic said:**
> Your settings are wrong - you have your internal IP pointing to your forum:

```
Firefox can't establish a connection to the server at 192.168.1.100
```That is a private IP and is not routeable over the internet.  You must have an external IP on the forum box and you hopefully already have some sort of firewall.

cheers Fragadelic,Now this is funny i spent 2 days looking for a solution to this problem and have just found this [http://ubuntuforums.org/showpost.php?p=1965165&postcount=1](http://ubuntuforums.org/showpost.php?p=1965165&postcount=1)
which i have just read and now understand what was wrong,which was what you just said,so cheers.

If you could try to connect again it should be ok now hopefully.

As for a firewall i have no idea,have you any suggestions,on what to read or do to secure my network,see i really thought this through :)

but cheers again for the help

---

### Post by Fragadelic on 2011-11-04
> **fubar2010 said:**
> cheers Fragadelic,Now this is funny i spent 2 days looking for a solution to this problem and have just found this [http://ubuntuforums.org/showpost.php?p=1965165&postcount=1](http://ubuntuforums.org/showpost.php?p=1965165&postcount=1)
which i have just read and now understand what was wrong,which was what you just said,so cheers.

If you could try to connect again it should be ok now hopefully.

As for a firewall i have no idea,have you any suggestions,on what to read or do to secure my network,see i really thought this through :)

but cheers again for the help

Forum is showing up now.  Good show!

---

### Post by fubar2010 on 2011-11-04
Well thanks again [Fragadelic]("http://ubuntuforums.org/member.php?u=386921") for the help :D

---

### Post by Fragadelic on 2011-11-04
> **fubar2010 said:**
> cheers Fragadelic,Now this is funny i spent 2 days looking for a solution to this problem and have just found this [http://ubuntuforums.org/showpost.php?p=1965165&postcount=1](http://ubuntuforums.org/showpost.php?p=1965165&postcount=1)
which i have just read and now understand what was wrong,which was what you just said,so cheers.

If you could try to connect again it should be ok now hopefully.

As for a firewall i have no idea,have you any suggestions,on what to read or do to secure my network,see i really thought this through :)

but cheers again for the help

There are a few firewall frontends in ubuntu that you could choose but you have to use one or you will get hacked.

---

### Post by fubar2010 on 2011-11-05
Ok cheers,i will look into it and see what i can do :D

---

