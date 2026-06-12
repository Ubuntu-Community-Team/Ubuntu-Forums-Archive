---
title: "HELP: Apache2 PHP5 Sybase"
date: 2007-05-16
forum: Server Platforms
---

### Post by squibbon on 2007-05-16
Can anyone tell me what should i do to make it worked? Please.

Installed:

[LIST]
[*]Apache2 (Synaptic)
[*]PHP5 (Synaptic)
[*]php-sybase (Synaptic)
[*]sybase-ase_11.9.2-4_i386 (Local Package)
[*]sybase-common_11.9.2-4_i386 (Local Package)
[*]sybase-openclient_11.1.1-4_i386 (Local Package)
[/LIST]

I can connect to DB server using isql. i can do queries:

************************************************************************

**$ isql -Sour_server -Uuser1 -P -Dour_db**

1> select first_name from personal where pers_id='82001'  
2> go
 first_name           
 -------------------- 
 ERICSON              

(1 row affected)

************************************************************************

I can't connect local DBs.

************************************************************************
**$ isql -Usa -P**

CT-LIBRARY error:
        ct_connect(): directory service layer: internal directory control layer error: Requested server name not found.

************************************************************************

I can load simple php pages but i can't make sybase_connect() work:

************************************************************************

Warning: sybase_connect() [function.sybase-connect]: Sybase: Client message: Server is unavailable or does not exist. (severity 78) in /var/www/dbconnect.php on line 2

************************************************************************

Please enlightened me.

---

### Post by craigp84 on 2007-05-17
Hi Squibbon,

Do you definately have a DataServer running on the localhost?

Show us your PHP code... are you specifying a hostname to connect to? Does it work when you specify the name of another DataServer?

Is your Sybase interfaces file setup ok?

-c

---

### Post by squibbon on 2007-05-17
This is my PHP code

> Do you definately have a DataServer running on the localhost?

 honestly, don't know to make localhost DataServer running.

 <?php
                $con = sybase_connect("our_Server", "user1", "");
                sybase_select_db("our_db");
                $qry = sybase_query("select * from department", $con);

                echo sybase_result($qry, 1, 1);

                sybase_close($con);
?>

also configured sybase interface file thru dsedit and succesfuly make queries thru **isql**.

can someone make a step-by-step instruction installing PHP5 APACHE2 along with sybase in ubuntu?

---

### Post by craigp84 on 2007-05-18
> honestly, don't know to make localhost DataServer running.

Ordinarily you would script this into a sybase-start,sh. It's pretty involved to get an instance going. Check out sybase's online help, it's pretty good - even if absolutely everything else in sybase world is sh1te (there's no decent DB client tools, it encounters deadlocks and reaps spids like crazy, you'll see a thread crash every other day, sometimes it'll just sit there, seemingly doing nothing!).

The only half-decent client side tool i've found is "sqsh" - handy to keep around.

As for your code, looks good to me, especially if you're able to isql -S our_server -S our_db -U xxx. Can you do this from the same box the PHP scripts are running from?

I couldn't do a step by step i'm afraid - i've never used PHP with it before. Maybe someone else could?

-c

---

