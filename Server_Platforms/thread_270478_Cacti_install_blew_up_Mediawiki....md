---
title: "Cacti install blew up Mediawiki..."
date: 2006-10-03
forum: Server Platforms
---

### Post by tdeboeser on 2006-10-03
Hi,
I have a server running a MRTG and Mediawiki.  Recently I found [Cacti]("www.cacti.net"), and thought it looked interesting.  Big bounus was it was 'apt-get'-able.  But its an interactive install, an of course I didn't pay attention.  

It seems Cacti requires PHP5, so... zombie like I just took all the defaults.  PHP4 was removed, along with Mediawiki.  Luckly the DB info wasn't dropped (i've made a backup :).  

Now I've reinstalled PHP4, the php4 apache2 module, and mediawiki. Apache seems happy now:
```

Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations

```

And I can get to my MRTG stuff. 

But when I try [http://*hostname](http://*hostname)*/mediawiki I'm asked to save the file "index.php".  In MS-IE I get the text of the file (php code).  I guessing apache isn't dealing with php right.
  
How can I make sure apache has the right pathing?  Or is my problem somewhere else?

Thanks,

Tom

Oh this is Ubuntu Dapper (6.06) on a compaq dl380.

---

