---
title: "MySql Injections"
date: 2009-09-05
forum: Security
---

### Post by phillw on 2009-09-05
Now, it's most likely I've got the wrong end of the stick here, but ...

the **"**  and **/**  etc. are treated somewhat differently in MySQL from the likes of A-Z, a-z, 0-9 etc. So far, so good....

The use of 
**[SIZE=2]mysql_real_escape_string[/SIZE]**

Strips these out, to prevent injection.

So far, so good.....

How do I allow some one to do a search of a  1/2" Widget ?
Oh, and by the way, said widget is also available in 3/16", 1/4", 5/8", 15/16" etc......

There are also 1/2" Thinggies - available in all sizes, along with 5/16" whatsits - also in all sizes.

I'm using LAMP, so it's PHP and MySQL ... could someone point me towards a tutorial that can teach me how to do this, safely & in a manner that I can actually learn. 

ID
Main Group
Sub Group
Item
Size
'picture'
Cost, Net, Sales price#1, #2, #3, #4

I've got the  fields Main Group, Sub Group, Item & Size within the table all on FULLTEXT search, and that works fine.

I'm on sort of nodding terms with MySQL - I can do the basic stuff of creating tables, adding / searching etc. from php. But I understand that allowing **"** s and **/** s free access is not such a good idea.

My current thinking is to set the database up so that after creating it and populating it, I would then delete that user and  leave one user that has read and select privalidges only, but, of course, I would still be able to add a new user to it to ammend it. At that point, I would take the database off-line (out of office hours), for the few minutes it takes to add / delete / amend entries and delete the user afterwards. (I'd be using phpmyadmin for the users bit)

So, when you've all stopped giggling (lol) - I'm sure there is a better way

Thanks,

Phill.

---

### Post by koenn on 2009-09-07
I think the common way to handle this is to 'sanitize' the input yourself i.e. in your program, before you use that input to build an SQL statement that you send to the database.

i.e. you 
- allow your users to input something like 1/2"
- you check that the value you retreive from the web form really is of the form <nothing>[0-9]/[0-9]"<nothing>
- if it is, you use it in a where clause that you send to the database 
- but if it isn't, you refuse to process it.

Some of this is built-in in PHP and other web scripting languages, some of it you'll have to add yourself or borrow from people who've posted their solutions on the web


Google: php sanitize input

Or go ask around in the Programming forum. Those guys should know how to deal with this.

---

### Post by The Cog on 2009-09-07
Stripping the special characters out is not goot because it means they cannot exist in the database. The normal thing to do is to "escape" them in some way. This is usually done by preceding them with another special character. For instance, the string "Godot's late." may be entered into the database by entering "Godot''s late." 

See this note:
[http://www.orafaq.com/faq/how_does_one_escape_special_characters_when_writing_sql_queries](http://www.orafaq.com/faq/how_does_one_escape_special_characters_when_writing_sql_queries)

---

### Post by DaithiF on 2009-09-07
AFAIK, the purpose of **[SIZE=2]mysql_real_escape_string[/SIZE]**[SIZE=2] is to escape these characters, ie. not strip them out.  So it should be entirely possible to pass input which includes those characters to a php webapp and not cause mysql any problems.
[/SIZE]

---

### Post by koenn on 2009-09-07
Well, it's true that special characters, especially quotes, can be problematic in a database because your SQL also uses quotes for values, so escaping those is necessary ,

but I think the OP is actually talking about sql injection attacks, where malicious users attempt to run their own  sql statements against the database by means of crafted input (which usually involves the use of quotes, / , ; , ...). 

see [http://en.wikipedia.org/wiki/SQL_injection](http://en.wikipedia.org/wiki/SQL_injection)

So he'll need to check / sanitize the input so that a query for '1/16" widget' is allowed, but anything appended to it is not (and so on).

---

### Post by phillw on 2009-09-07
> **koenn said:**
> Well, it's true that special characters, especially quotes, can be problematic in a database because your SQL also uses quotes for values, so escaping those is necessary ,

but I think the OP is actually talking about sql injection attacks, where malicious users attempt to run their own  sql statements against the database by means of crafted input (which usually involves the use of quotes, / , ; , ...). 

see [http://en.wikipedia.org/wiki/SQL_injection](http://en.wikipedia.org/wiki/SQL_injection)

So he'll need to check / sanitize the input so that a query for '1/16" widget' is allowed, but anything appended to it is not (and so on).


Yeah ... That sort of thing. A user with select only privalidges can still issue a select statement, such as

SELECT grantee, privilege_type, is_grantable FROM information_schema.user_privileges WHERE privilege_type = 'SUPER'; 



(Try it some time !!!)


But, as i do not have parts called  'grant*', privalege, schema, information (I think the important one being the schema and information in information_schema) - if I actively look for these, would it be enough to leave the information_schema safe ?


It would also stop this one ...

SELECT schema_name FROM information_schema.schemata;

I'd have to check for 'data'  to stop this one .......

SELECT @@datadir; 

[http://pentestmonkey.net/blog/mysql-sql-injection-cheat-sheet/](http://pentestmonkey.net/blog/mysql-sql-injection-cheat-sheet/)

gives a fuller list of the sort of stuff that I'd have to watch out for.

Converting to decimal is not too easy as we have an exceedingly annoying measurements called  1/3" and 2/3" !!!!

Although, one the plus side - we don't have any parts called **SELECT** which does seem to negate the majority of those problems. 

Writing a filter to stop a case insensitive **SelEct** would be do-able for me - I'd still have to look up how to do it in PHP - but, I know it's perfectly possible.
 
On the same note, I guess it would be possible to check anything with an **"** or **/** character against a list of allowable fractions ?

Thanks for your comments - they've given me food for thought.

Phill.

---

### Post by movieman on 2009-09-07
The simple answer is that you should never, ever generate a query string from user-supplied data on the Web; trying to ensure that a query string generated from arbitrary data will not allow an attacker to exploit your database is fraught with problems.

---

### Post by koenn on 2009-09-07
> **phillw said:**
> Yeah ... That sort of thing.  ....
What you're trying to do is blacklisting : you try to eliminate anything suspicious. 

Whitelisting is usually more efficient : you accept only what you expect, and throw away anything else.
That means you check (and possibly modify) every value that is supplied by the users
eg:
If an input field in your app serves to input a quantity, you only accept integers (so any appended string will make it fail)
if your sizes are fractions of an inch, you only accept <integer>/<integer> (you can possibly add the " yourself, if that's required to match the values in the database.

In addition to that, you can still blacklist suspicious characters in strings ( ; =  @  AND OR  ...) in stead of blacklisting every SELECT or other statement that could be appended by using one of these characters


And, re what movieman says, you can try to avoid arbitrary ("free text") input from the users by having dropdownlists, selection boxes, ... with predifined values. Goes a long way to keep users honest. 


and thanks for the cheat sheets  :)

---

### Post by phillw on 2009-09-07
I think, on reflection, that I may strip out the fractions etc ...

If they search for widget - they get a list of all sizes presented to them in a table - that way, I can keep track of the ID for if the prices are ever put on.

Once I learn how to safely handle fractions and inches I can add it. I think better to err on the side of caution.

As for the cheat sheet - that was a simple google, but it's nice to have a list of the 'usual suspects' for testing with.

Again, thanks everyone for 'talking' this one through with me.

:P

Phill.

---

### Post by bobince on 2009-09-08
> How do I allow some one to do a search of a  1/2" Widget ?Actually the double-quote " is not problematic in SQL string literals, because the delimiter is the single-quote. Whilst MySQL by default allows you to use double-quotes for string literals, you shouldn't do this. It means something else in ANSI SQL, and who knows, maybe your MySQL server is using ANSI mode.

A better example of a troublesome string is the name O'Reilly. It's got a single-quote (apostrophe) in it, but don't strip it out, because stripping characters is lame, and Mr. O'Reilly will be cross if you mess up his name.

Instead, as you said, you use mysql_real_escape_string:

```
$name= "O'Reilly";
$query= "SELECT * FROM people WHERE name='".mysql_real_escape_string($name)."'";
```expands to:

```
SELECT * FROM people WHERE name='O\'Reilly'
```Which is fine. All 'troublesome' characters get correctly escaped for the context you're putting them in, you don't have to strip them out, and everyone's happy.

Tedious technical side note: actually the above expansion, again, isn't valid ANSI SQL and would go wrong in ANSI mode, where a doubled-apostrophe is expected like The Cog mentioned. But you don't have to worry about that! You're using mysql_real_escape_string, which knows what mode its database is in and works it all out for you.

However, you may have noticed that typing '".mysql_real_escape_string()."' every time you want to put a string literal in from a variable is a real pain. So a better solution is to avoid making your queries out of bits of string stuck together, and instead use mysqli with [parameterised queries]("http://de.php.net/manual/en/mysqli.prepare.php"), which do all the escaping work for you.

    ```
$query= $mysqli->prepare('SELECT * FROM people WHERE name=?');
$query->bind_param('s', $name);
```

---

### Post by phillw on 2009-09-08
Many thanks ...

So, let me just check ...

A part is stored as

MGJPartNo:  WJ34
Master Group: Iron Parts
Description: Widget
Dimensions: 3/4"
.
.
.


A customer types in **3/4" Widget** in the little search window, which I end up with in a variable called $test.

To carry out the FULLTEXT search, my command looks like this, where
    $fulltext='(MGJ_Part_No,OEM_Part_No,Master_Group,Sub_Group,Description,Dimensions)';

$q="Select * from $table where match $fulltext against $test order by ID";
$rs=mysql_query($q) or die(mysql_error());
$nr = mysql_fetch_array($rs);

So, I'd just need to convert it to .....

$query= "SELECT * FROM $table WHERE MATCH $fulltext AGAINST '".mysql_real_escape_string($test) ORDER BY ID ."'";
$rs=mysql_query($q) or die(mysql_error());
$nr = mysql_fetch_array($rs);
  
?  
Would this be sufficient to stop injections ?

Thanks,

Phill.
P.S., the 'die' error command will be tidied up - it's there for de-bugging !!

---

### Post by koenn on 2009-09-08
any specific reason you'd do FULLTEXT and not something along the lines of

```
 select * from $table where Description='Widget' and Size='3/4' ; 
```


?

---

### Post by phillw on 2009-09-08
RE: the search,

there are 40+ parts in a carburetter for a Stihll TS400 chain saw,
there are 50+ parts in the engine, ignition module, water kit......
there are several makes & models of chain saw !!!
(And  that, for example is just one line of spares)

Nuts, Bolts & washers are "served" in flavours of metric, imperial UNC, imperial UNF etc.
with different shapes of heads (nut, rounded, single slot, cross-head...) the bolts are available in the same thread and width, but different lengths .... Oh, it's fun ....
Engine oil is available in different SAE numbers, in different quantities ....
There's air filters, oil filters, fuel filters ......

If someone types in the part number, it must find it. If some-one types in "TS400 carburetter", it must find them all. If some types in TS400 - It'll return one **long** parts list, which is to be sorted by sub-section, then by part description, then by size.
If someone types in "carburetter ts400", like-wise, it must still find them. Humans are un-predictable beasts - and engineers are their own special sub-species !!!!

Hence the rather horrendous

    $fulltext='(MGJ_Part_No,OEM_Part_No,Master_Group,Sub_Group,Description,Dimensions)';

I was keeping it 'simple' as it was the issues of **/** and **"** that were causing me headaches !!!

Anyone want to swap ? - lol

Phill.

---

### Post by koenn on 2009-09-08
hm, i see. I'd think an engineer, or someone capable of doing engine work on a chain sow, would at least know to distinguish between make, model, part, size, ...  - but it's your call, of course.

and no, I don't want to swap :)

just thinking that if you can classify the data more precisely, your search would be more performant and the user input easier to control ... and your search slightly less user friendly.

---

### Post by phillw on 2009-09-08
[SIZE=2]> **koenn said:**
> hm, i see. I'd think an engineer, or someone capable of doing engine work on a chain sow, would at least know to distinguish between make, model, part, size, ...  - but it's your call, of course.
and no, I don't want to swap :)
just thinking that if you can classify the data more precisely, your search would be more performant and the user input easier to control ... and your search slightly less user friendly.
"Have you got one of them **gasket** thinggies that goes between the **engine** & **manifold** on an... erm.... hang on ........................... oh, yeah a **DPC6410** ?" 
*"What year ?"*
"How do I find that out ?"
*"The serial number is stamped on the engine block"*
*" *Hang on.......................................................................................................  Nope, it's corroded off"
Sort of gives you an idea !!!!
There are only about 10,000 parts- no more than 5 - 10 users max at once. MySQL will (fingers crossed) be able to handle that. 
I'm hoping to have it so that the search picks out the words in [/SIZE][SIZE=2]**BOLD** [/SIZE][SIZE=2]from when they type it in like that ignoring the bits it doesn't like (evidently it ignores 'the' 'one', etc & I can add to its list!!!
[/SIZE][SIZE=2] (It took me 5 days to learn about the basics of what it can & can't do)
[/SIZE][SIZE=2] FULLTEXT seems to be my best hope :eek:[/SIZE]
        [SIZE=1][SIZE=2]
When it can find the answer to **3/4" UNC 50mm Bolt **then I'll know it's working !!!

If you want to have a giggle, have a look at 

[http://mgjuddltd.co.uk](http://mgjuddltd.co.uk)

They're there just to give a bit of "look & feel", they're static pages, but the catalogue is going to be dynamicially done, as there are new parts coming out all the time. The other reason for that being there, was for me to learn CSS, how to do 'roll-over' buttons in CSS and set up the print CSS without the nav-bar on the left. (It works, try printing a page !!)

As you will see, from the left hand column - there are a lot of sections just to do on there - a SEARCH is really needed.

That's just part 1 - part 2 has all the nuts, bolts, washers, glue, files, spanners, welding-sets etc!!!!
From memory, there's about 200 types of spark-plug, 50 heater-plugs....

The scaling up is of no major concern - that's what MySQL is for - If it will work with 100 parts, it'll work with 10,000 :)

Doing the whole site 'static' then indexing it - then re-doing it as parts are added / deleted / replaced was a non-starter (Hence the reference to CD on the home page).

Interesting times for me - when I was trying it on my laptop (piglet) I set it up as a server, but messed up the security and got hacked. 

Going to be MUCH more careful this time. PIglet will still be my test bed for mysql injection tests - the crib-sheet will be of help in carrying them out.

Thanks for your interest :)

Regards,

Phill.

P.S. the above is just to explain why I'm doing FULLTEXT - This is a security forum, not a web-design forum - I simply explain so as you can all see what it is I am aiming for. The last couple of posts seem to have wandered off topic, please Mr/Mrs/Miss/Ms moderator - don't shout at me. I think I've explained enough of what I need to do so as those knowedgable of how to protect from MySQL injections in this case have all the information they need, instead of asking for further information.[/SIZE] 
[/SIZE]

---

### Post by bobince on 2009-09-09
> Would this be sufficient to stop injections ?

As long as $fulltext and $table are controlled by you and known-safe, yes.

You have to do this every time you drop an unknown string into a query. It soon gets tedious and it's easy to miss one, which is why parameterised queries are generally good news.

---

### Post by unutbu on 2009-09-09
What if phillw were to write a function sanitize() which removes all MySQL keywords and syntax symbols (e.g. SELECT, UPDATE, DELETE, ';', etc) from $text? Then, whenever input is taken from the user, he could just run it through sanitize() before passing it on to mysql_query.

Would that be a satisfactory method of preventing injections?

---

### Post by phillw on 2009-09-09
> **bobince said:**
> As long as $fulltext and $table are controlled by you and known-safe, yes.

You have to do this every time you drop an unknown string into a query. It soon gets tedious and it's easy to miss one, which is why parameterised queries are generally good news.

Thanks guyz & galz.  As the 'search for' bit will be a form on another page, then passed as $test - I will have control over everything except whatever they enter in the form. Once I have the returned results I can then do the tidying up of things like 0 records found, the returned result >50% database (which I believe also returns 0 records) and most importantly - keep the script kiddies at bay :-\

I've just got to make the output look 'pretty' now - but I have the template ready for that :-)
Probably have to alter it now that I've decided to verify to XHTML strict.
(Just got the front page verified - had to alter a couple of things for it)

That & 'mail to:' are the only bits that will require user input - I've seen some stuff already on protecting mail to:  within PHP.

Once again, thanks to everyone.
When the code is finished I will be offering it, fully commented, as a tutorial - To save blushes and missing anyone out, I will just list the sites that I got help with it.

Phill.

Phill.

---

### Post by phillw on 2009-09-09
I'm still digging & came across this ...

```

<?php 
// Function for safety 
function quote_for_safety ($value) 
{ 
if (get_ magic_quotes_gpc()) {         
$value = stripslashes($value);   //if magic quotes is enabled remove those extra slashes  
} 
// if the value passed is not integer Quote it 
if (!is_numeric($value)) { 
$value = "'" . mysql_real_escape_string($value) . "'"; 
} 
return $value; 
} 
 
$db_name="dev";  // Database name 
$connection=mysql_connect("localhost","root","")  
or die("I couldn't connect");  
$db=mysql_select_db($db_name) or die("I couldn't select your database"); 
 
// Make a safe query 
$SQL = *sprintf("SELECT * FROM users WHERE user=%s AND password=%s", 
quote_for_safety($_POST['username']), 
quote_for_safety($_POST['password'])); 
 
Mysql_Query($SQL, $connection); 
?>     

```I leave it in its entirety - magic-quotes are not recommened these days !!

According to where I got it from ....

```

 [COLOR=darkred]sprintf()[/COLOR] is used to format data and put it into a string array. It is equivalent to printf function in &#8216;c&#8217; language which includes escape sequences and format identifiers. 

```on php.net there is this little snippet (amongst other stuff, that is WAY over my head)

The article can be found here ...     [http://www.dev-exchange.com/cms_view_article.php?aid=10](http://www.dev-exchange.com/cms_view_article.php?aid=10)

```

I created this function a while back to save on having to combine mysql_real_escape_string onto all the params passed into a sprintf. it works literally the same as the sprintf other than that it doesn't require you to escape your inputs. Hope its of some use to people

<?php
function mressf()
{
    $args = func_get_args();
    if (count($args) < 2)
        return false;
    $query = array_shift($args);
    $args = array_map('mysql_real_escape_string', $args);
    array_unshift($args, $query);
    $query = call_user_func_array('sprintf', $args);
    return $query;
}
?>

Regards
Jay
Jaygilford.com

```The usual question....

Does it **ADD **to protection, make no difference or make it worse (The 1st example I can follow, the 2nd one you'd have to tell me is worth learning how it works)...

Phill.

---

### Post by bobince on 2009-09-10
> **unutbu said:**
> What if phillw were to write a function sanitize() which removes all MySQL keywords and syntax symbols (e.g. SELECT, UPDATE, DELETE, ';', etc) from $text?

Then he wouldn't be able to put the word &#8220;delete&#8221; in the name of anything in his database; or anything containing a semicolon, or a product name like &#8220;select cuts of beef&#8221;.

This does not seem like a win to me.

There is already a function that will take any string and make it safe to put in a MySQL string literal. That function is called &#8216;mysql_real_escape_string&#8217;. If you use that function in the places you need it, you are safe and filtering out perfectly valid words that happen to be SQL statements is pointless. If you don't use that function, using an alternative function that doesn't really know SQL syntax but randomly tries to remove words you think are bad won't help you at all, you'll still be vulnerable.

Indeed, in most MySQL interfaces including PHP's, you cannot chain two statements using a &#8216;;&#8217; character, so trying to filter on &#8216;;&#8217; or statement names like &#8216;SELECT&#8217; would be utterly futile. The characters you need to take care of are the apostrophe and the backslash, and in certain obscure cases non-ASCII and control characters. The function to get that right is &#8216;mysql_real_escape_string&#8217;. Any ad-hoc function you care to come up with yourself is almost certainly going to be wrong for some input.

> **phillw said:**
> Does it **ADD **to protection, make no difference or make it worse (The 1st example I can follow, the 2nd one you'd have to tell me is worth learning how it works)...

The quote_for_safety example uses mysql_real_escape_string, which is GOOD and THE RIGHT THING.

However, it also tries to undo a dose of magic_quotes_gpc. Now admittedly no-one should ever be using magic quotes, as they're broken idiotic rubbish that even the PHP devs who came up with them have been telling us not to use for years, but if you were to add code to your script to detect the damage that magic quotes do and undo it, this would be the wrong place to do it.

This, and a lot of other broken PHP &#8220;security&#8221; code makes the assumption that any time you're using $_GET/$_POST/$_COOKIE/$_REQUEST (gpc) data you're always putting it in a database, and any time you're putting something in a database it must be from gpc data. That's bull though. If you just had a plain string &#8216;POTATO\\LEMON&#8217; in your script, or you read it from an XML file, or you grabbed it out of another database table, it *won't* have been mauled by magic quotes, so attempting to correct for that mauling would leave you with &#8216;POTATO\LEMON&#8217;, which is not the string you started with. This isn't in itself a security error, but it's a common bug to see poorly-written applications either swallow backslashes, or needlessly duplicate them, to the point where they double up on every edit, leaving you with page names like &#8220;My page\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\'s nice&#8221;.

So if you *must* correct for magic_quotes_gpc(*), the place to do it is right at the top of the script, iterating over the arrays in question replacing every value with one with fewer slashes in. **Don't** attempt to also do MySQL escaping at this point, because you don't know that a submitted string is about to go into the database. Maybe you'll spit it straight out to a web page, or write it to an e-mail, or log it to disc. In this cases you don't need any MySQL escaping and doing so anyway will result in loads of weird slashes all over your output.

The golden rule: keep your strings in raw, unescaped format until such time as you need to escape them to put them into another string.

If you remove the magic quotes fixing from that function, all that's left is `mysql_real_escape_string`. Which you should use instead.

(*: my preferred approach is to sniff for magic_quotes_gpc, and if present immediately die with an error message telling you not to use that, you big old fool. It may not be very user friendly, but I've spent enough time fixing naïve vulnerable PHP apps that I no longer greatly care about being friendly.)

 The second example (mressf) is a little bit of syntactical sugar to make calling mysql_real_escape_string a bit easier, if you are comfortable with printf-style substitutions. It's fine.

Did I mention parameterised queries? They'll stop you from having to think about any of this string-escaping stuff. Parameterised queries. Yay.

---

### Post by phillw on 2009-09-11
> **bobince said:**
> 
(*: my preferred approach is to sniff for magic_quotes_gpc, and if present immediately die with an error message telling you not to use that, you big old fool. It may not be very user friendly, but I've spent enough time fixing naïve vulnerable PHP apps that I no longer greatly care about being friendly.)


Magic quotes are turned off be default in my installation of PHP (I think that is the case in all v5 versions of PHP - But, I did check that they were off !!). Even in my 'noobiness' I could see that they were a BAD idea !!

For my needs there are 2 forms of user input


[LIST=1]
[*]The database search for parts
[*]email
[/LIST]
I was looking at the options of how to **SAFELY** send the result to the module that will be doing the display & pagination.

I looked at $POST and $GET - but am a little wary of any possible manipulation on it's way from one module to the another, even though there would be no more SQL stuff - I'd not like them to force a PHP script error that I hadn't thought of. 

The next idea is to make $display (an array) a global variable.
[RIGHT]
[/RIGHT]

[LIST=1]
[*] either global $display
[*]use the $GLOBAL function
[/LIST]
If I were to do this, I can either


[LIST=1]
[*]build all the display information into it
[*]Just build it with the ID's of the records matched, then do a 2nd MySQL Search in the display module. I'm not to keen on this, as it means re-opening the database connection & getting the 
individual records 1 at a time.
[/LIST]
I looked up what my limits on array size are and it is in the order of 100,000 records - I only have 2,000 records in the entire database - So, very much doubt I'm going to fall over that particular hurdle - plus, of course, in my iteration of using FULLTEXT, you cannot return more than 50% of the database anyway !

I know I am wandering towards the finer esoterics of programming, but I'd rather learn 'good' practices & stick with them than secure the MySQL bit, only to fail miserably because of a 'hole' when I'm dealing with returned result !!

As always, thanks for all your comments.

Phill.

---

### Post by phillw on 2009-09-11
```

[COLOR=#000000][COLOR=#0000bb]$link [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]mysqli_connect[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"localhost"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"my_user"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"my_password"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"world"[/COLOR][COLOR=#007700]);

[/COLOR][COLOR=#ff8000]/* check connection */
[/COLOR][COLOR=#007700]if ([/COLOR][COLOR=#0000bb]mysqli_connect_errno[/COLOR][COLOR=#007700]()) {
    [/COLOR][COLOR=#0000bb]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"Connect failed: %s\n"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]mysqli_connect_error[/COLOR][COLOR=#007700]());
    exit();
}

[/COLOR][COLOR=#0000bb]$city [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#dd0000]"Amersfoort"[/COLOR][COLOR=#007700];

[/COLOR][COLOR=#ff8000]/* create a prepared statement */
[/COLOR][COLOR=#007700]if ([/COLOR][COLOR=#0000bb]$stmt [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]mysqli_prepare[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$link[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"SELECT District FROM City WHERE Name=?"[/COLOR][COLOR=#007700])) {

    [/COLOR][COLOR=#ff8000]/* bind parameters for markers */
    [/COLOR][COLOR=#0000bb]mysqli_stmt_bind_param[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$stmt[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"s"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]$city[/COLOR][COLOR=#007700]);

    [/COLOR][COLOR=#ff8000]/* execute query */
    [/COLOR][COLOR=#0000bb]mysqli_stmt_execute[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$stmt[/COLOR][COLOR=#007700]);

    [/COLOR][COLOR=#ff8000]/* bind result variables */
    [/COLOR][COLOR=#0000bb]mysqli_stmt_bind_result[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$stmt[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]$district[/COLOR][COLOR=#007700]);

    [/COLOR][COLOR=#ff8000]/* fetch value */
    [/COLOR][COLOR=#0000bb]mysqli_stmt_fetch[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$stmt[/COLOR][COLOR=#007700]);

    [/COLOR][COLOR=#0000bb]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"%s is in district %s\n"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]$city[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]$district[/COLOR][COLOR=#007700]);

    [/COLOR][COLOR=#ff8000]/* close statement */
    [/COLOR][COLOR=#0000bb]mysqli_stmt_close[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$stmt[/COLOR][COLOR=#007700]);
}
[/COLOR][/COLOR]

```Now, which bit am I not understanding ....

How is the above safer than

```

[COLOR=#000000][COLOR=#0000bb]
$city [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#dd0000]"Amersfoort"[/COLOR][COLOR=#007700];[/COLOR][/COLOR]

$query= "SELECT District FROM City WHERE name='".mysql_real_escape_string($city)."'";
$rs = mysql_query($query)
.
.


```

I do know about using mysqli_connect for connecting - I had forgotten to code it in ... Ooops :(

Sorry for driving you all nuts - I just cannot get my head round it.

Phill.

---

### Post by bobince on 2009-09-11
> **phillw said:**
> How is the above safer than mysql_real_escape_string?

It's not; they're both equally secure. The only problem with the mysql_real_escape_string method is that it's very easy to accidentally forget to include one, as PHP encourages you to write queries like &#8220;WHERE thing=$thing&#8221;. And if you have a query with lots of parameters it can get quite hard to read if there are loads of mysql_real_escape_string() calls. (This problem can be mitigated by making a wrapper function with a shorter name like m().)

> printf("%s is in district %s\n", $city, $district);That'll be problematic if there can be a less-than sign or ampersand in either name. Maybe not too likely in this case, but in general any string you output to an HTML page should be escaped on the way out using htmlspecialchars:

```
printf("%s is in district %s\n", htmlspecialchars($city), htmlspecialchars($district))
```However, I usually save myself some typing and define a:

```
function h($text) {
     echo(htmlspecialchars($text, ENT_QUOTES)); 
}
```So I can then say in templates:

```
<p> <?php h($city) ?> is in district <?php h($district) ?> </p>
```

---

### Post by phillw on 2009-09-11
Thanks bobince

::SIGH:: 

I've lost track of what I wanted to do - I've leaned loads, so it has been good ...

This is a killer noobie question ....

I have my little form to post the user input to 'search.php' as the action ...

search.php looks like this ...

I'm sorry to include the whole code, but didn't want to try and remove bits I may have thought were not important and then be asked further questions ....

```

<?php
global $count;
global $result;
global $rpp;
global $test; 

 

$result = array();

    $rpp = 7;    //Records Per Page - 10 is a good number, You may need a lower number if some rows are 
                        // wrapping text to be 2 lines long --- have a play !!!! 
    $count = 0;   //Used to build the display array 
    /////////////////////////////////////////////////////////////////////////////////
    //Database connection
    /////////////////////////////////////////////////////////////////////////////////
     $host="localhost";  // the path to the database, usually localhost, 
                                 // but you can change this to wherever the database is,
                                 // e.g.  ******* To Be DONE *****    
    $user="Guest";  // your login name, for this part set up a 'read' only user, as there is little
                            // error checking 
    $password="Guest"; // the password you set - no password is dangerous !!! 
    $database="MGJuddLtd";  // The database you want to read
    $table="MGJ_Parts";        // The MAIN (Or only table within the database you want to read) 
    $table2="Images";        // The 2nd table - This is where I store the images (Pictures, in jpg format
                                    // that will be read when the user clicks on the 'MGJ Part No'
    $fulltext='(MGJ_Part_No,OEM_Part_No,Master_Group,Sub_Group,Description,Dimensions)';
                            // the above one is used for the fulltext search of the parts database
    $test="('equal')";        // test variable for full text search
    // to be replaced with GET_
   

    @mysql_connect($host,$user,$password) or die ("Unable to Connect to Server");

    @mysql_select_db($database) or die( "Unable to select database");
    /////////////////////////////////////////////////////////////////////////////////

    $q="Select * from $table where match $fulltext against $test order by ID"; //Master_Group,Sub_Group,Description,Dimensions";   
        
    $rs=mysql_query($q) or die(mysql_error());
    $nr = mysql_fetch_array($rs);
     // populate $result    
while ($row = mysql_fetch_array($rs)) {
     $result[$count] = $row;    
    echo $row['MGJ_Part_No'];  // debug
    echo $row['Master_Group']; //debug
    echo $row['Description'];  //debug
    echo $row['Dimensions']; //debug
    echo "<br />"; //debug
    $count = $count + 1; // Total Number of rows returned 
}     
 print $count;  //debug
 echo "<br />"; //debug
 
     $np = round ($count / $rpp);    //Calculate Total number of pages 
     
     
/// Time to build & display our results     
     
     ?> 


```

When you have all finished ripping the above to pieces...  
Is it safe ?

the display bit starts like this ....

**display.php**

```

<head>
<title>M.G. Judd Ltd. - Display Search Result</title>
<link rel="stylesheet" media="screen" type="text/css" href="mgj.css">
<style type="text/css">
@import "mgj_print.css" print;
</style>

</head>
<!-- Now, I'm using stuff from my CSS here - the font command in HTML is being phased out,
please feel free to use my CSS (They're extensively commented - just email me to phillw at uk dot vpolink dot com and
I'll gladly send them under the GPL license -->
<?php
global $count;
global $result;
global $rpp;
global $test; 

    
    
    @ $cps;        //Current Page Starting row number
   @ $lps;        //Last Page Starting row number
   @ $nr;
// now, you have the choice, a bit further down to choose either "showing x of y PARTS
// (or items, people ... etc) -  Just change the text Parts in the area marked 
// OR showing x of y PAGES - I guess you could do both, if you wanted ??!!!! 
   @ $a;        //can be used to print the current starting row number to be shown in the page
   @ $b;         //can be used to print the ending row number to be shown in the page
    @ $ap;            //can be used to print the current page number to be shown in the page
    @ $np;            //can be used to print the total page number to be shown in the page 
     $np = round ($count / $rpp);    //Calculate Total number of pages 
    @ $display;  // We're going to build this by slicing up $result
    
 /////////////////////////////////////////////////////////////////////////////////
    //Following IF Statement is used to make sure when the page is loaded for the
    //first time, Current Page's Starting row number is 0, i.e. 1st row from the
    //table is being printed. It will change as the user will click on next.
    /////////////////////////////////////////////////////////////////////////////////   

. . 
..
..
..


```

Now, display.php is going to call itself when the user presses next / previous - I have no problem sorting that out. But, how the heck do I get 'search.php' to call 'display.php' ..... This may sound incredibly dumb, but I have searched for a command to put at the end of search.php to pass control over to display.php  
:confused:

Originally, as I have no doubt mentioned, the display and search were one self-calling page with LIMIT, I can't use that with FULLTEXT  :-(

It's only one little search php, to be used on every page - I'll work out the esoterics of carrying over what page they were on later, at the moment - when they've done searching, they can go back to the main page !!!

Please don't shout at me ... from my 1st posting on this thread, I have learnt SO much - thanks to everyone who will take a minute out to explain something, for that - Thanks.

Phill.

---

### Post by phillw on 2009-09-13
I know this is "programming bit ... but ...

```


$q= "SELECT * FROM $table WHERE match $fulltext against $test order by ID";
        
// $q= "SELECT * FROM $table WHERE match $fulltext against '".mysql_real_escape_string($test)."' order by ID";   

```$q works fine,
the // one does not 

I'm guessing I've missed out a ' or a " somewhere ... but I cannot see where ...  :(

---

### Post by bobince on 2009-09-14
> **phillw said:**
> $q= "SELECT * FROM $table WHERE match $fulltext against '".mysql_real_escape_string($test)."' order by ID"; // doesn't work

Yeah, that's because $test isn't a plain text search term, you've already wrapped it in some SQL syntax:

> $test="('equal')"

You either want:

```
$test= "('equal')";
$q= "SELECT * FROM $table WHERE match $fulltext against $test order by ID";
```

or:

```
$test= 'equal';
$q= "SELECT * FROM $table WHERE match $fulltext against ('".mysql_real_escape_string($test)."') order by ID";
```

If you are planning to match user-submitted strings then presumably the second is the way to go.

---

### Post by phillw on 2009-09-15
Thanks, I did finally get my head round it !!!

I needed to 

```

$test = mysql_real_escape_string($test);  
$q= "SELECT * FROM $table WHERE match $fulltext against ('$test') order by ID";

```where 

$test = "equal"

these **. ' / **" and **\**  will be the death of me !!!

Now it won't find **3/4"** ......  then min length for ft searches is 3, so I'm okay there. It escapes as [B]3/4\"
[/B]But, my dataas inputted was not escaped when I wrote it to the db. I'm guessing that I should have ?

Phill.

Added ...

It will not find **3/4"** with real_escape commented out, either.

---

### Post by phillw on 2009-09-15
Thanks, I did finally get my head round it !!!

I needed to 

```

$test = mysql_real_escape_string($test);  
$q= "SELECT * FROM $table WHERE match $fulltext against ('$test') order by ID";

```where $test = "equal"

these **. ' / **" and **\**  will be the death of me !!!

Now it won't find **3/4"** ......  then min length for ft searches is 3, so I'm okay there. It escapes as [B]3/4\"
[/B]But, my dataas inputted was not escaped when I wrote it to the db. I'm guessing that I should have ?

$test = '%3/4"%'
```

$test = mysql_real_escape_string($test);  
$q = "SELECT * FROM $table WHERE Dimensions LIKE '$test'";  

```Escapes out %3/4"% to %3/4\"%  but finds it okay ....


> SELECT * FROM MGJ_Parts WHERE Dimensions LIKE '%3/4\"%'
[ I'm echoing  ID, Part No., Description, Dimensions and $count]
15MC/2/9Malleable Iron FittingsMale - Female Reducing Socket
(1) 1", (2) 3/4" BSP, a = 55 mm
1
16MC/3/9Malleable Iron FittingsMale - Female Reducing Socket
(1) 1 3/4", (2) 1" BSP, a = 60 mm
2
21AC/FS34Malleable Iron FittingsFemale Equal Socket
3/4" BSP
3
31AC/MN34Malleable Iron FittingsEqual Hexagonal Nipple
3/4" BSP
4
40MC/34/10Malleable Iron FittingsCap
3/4" BSP
5
48MC/34/11Malleable Iron FittingsHollow Plug
3/4" BSP
6
58MC/34/12Malleable Iron FittingsBack Nut
3/4" BSP
7
:-(


Phill.

---

### Post by bobince on 2009-09-15
> **phillw said:**
> But, my dataas inputted was not escaped when I wrote it to the db. I'm guessing that I should have ?

No. You escape data to fit out-of-band characters into an SQL statement itself. Once the database server has read in the statement, decoded the data and put it in the database, they are just normal characters. They're not stored in any ‘escaped’ form inside the database itself.

> It will not find **3/4"** with real_escape commented out, either.If we're talking MySQL fulltext search then no, it never will. Fulltext search is based on words, where MySQL's default idea of a word is something that's at least 4 letters long, with no punctuation in the middle, and not matching a list of ‘common’ stop-words like “the”. (MySQL's default stopwords list is annoyingly long and [includes many things you wouldn't expect to be described as ‘common’ words]("http://dev.mysql.com/doc/refman/5.1/en/fulltext-stopwords.html").)

You can to some extent [reconfigure MySQL's fulltext properties]("http://dev.mysql.com/doc/refman/5.1/en/fulltext-fine-tuning.html"), but it's never really going to do a good job of matching arbitrary strings like “3/4"”. That sort of thing could only really be found using a LIKE search, but then you'd be doing an unindexed full-table scan.

---

### Post by phillw on 2009-09-15
This does appear to be the case :-(

Even if I turned down ft_min_len = 1, I'm not going to easily find a host that will allow it !! 

[http://www.databasejournal.com/features/mysql/article.php/1587371/Using-Fulltext-Indexes-in-MySQL---Part-2-Boolean-searches.htm](http://www.databasejournal.com/features/mysql/article.php/1587371/Using-Fulltext-Indexes-in-MySQL---Part-2-Boolean-searches.htm)

with boolean does give a glimmer of hope. One bit i picked up on my trawls on the subject is to set the ignored word list to /dev/null  - that way it can't add any words on its own ;-)

I guess I'm going to have to consider searching $test for allowed fractions and metric sizes, and then do a secondary LIKE search of the Dimensions column with LIKE. Which is deffinately NOT what I wanted to be doing. (To say nothing of knowing enough of php string handling to start searching $test with a varied selection of blooming fractions).
This is turning into a nightmare !!!!
I *guess* there is a way to find the string position of a **"** and then count backwards untill I hit a white space, or start of string. But that's way out of my limited understanding of string handling in php (Be dead easy for me in QBasic - lol).......

Hmmm... paramatisation .... A pop-down box with a list of $size ( 1/8", 1/4", 15/16" ...... and 1mm, 1.5mm, 2mm etc) ... I am thinking aloud, but could I then nest the selects ?

I can see nesting is possible, but that is beyond my knowledge atm. I'd basically be trying to 
SELECT * FROM (SELECT * FROM $table WHERE match $fulltext against ('$test')) WHERE Dimensions LIKE '$size' ORDER BY ID

And, I KNOW that syntax is going to miles wrong - but, in theory, could it work ?

BTW, as ever, bobince - thanks for bearing with me !!

Phill.

---

### Post by bobince on 2009-09-16
> **phillw said:**
> with boolean does give a glimmer of hope.

I always use boolean mode searches, but it still doesn't let you around MySQL's limitations on what constitutes a word.

> A pop-down box with a list of $size ( 1/8", 1/4", 15/16" ...... and 1mm, 1.5mm, 2mm etc) ... I am thinking aloud, but could I then nest the selects ?Well if you've got a number of predefined values for $size, you can surely just use &#8216;=&#8217; to match and not bother with LIKE or fulltext? Then you can use a normal index and it'll be nice and fast.

> SELECT * FROM (SELECT * FROM $table WHERE match $fulltext against ('$test')) WHERE Dimensions LIKE '$size' ORDER BY IDYou *can* do subqueries, but I don't see why you'd need to. The above would be equivalent to:

```
    SELECT * FROM $table
    WHERE MATCH $fulltext AGAINST ('$test')
    AND dimension='$size'
    ORDER BY id
```This is assuming you're trying to narrow down the fulltext results by matching only parts of the right size. If your aim was actually to match the $size string within the size column as well as in the fulltext index, you'd use &#8216;OR&#8217; instead of &#8216;AND&#8217;.

Note that LIKE without special characters is just the same as &#8216;=&#8217; (only slower). If you want a substring match, you'd say:

```
    AND dimension LIKE '%$size%'
```And then a $size of &#8220;3/4"&#8221; would match the size &#8220;203/4" and a bit&#8221;.

---

### Post by phillw on 2009-09-16
Thanks, yeah ... it's sort of looking like OR ....  I see what you mean about 3/4", but, as I have things like 2 1/2"  inch, I'm deffinately up the creek without a paddle :-\

I don't know of a way round that, except using a pop down list which displays **1 1/4"**  but searches for **1.25"  **I'm going to need it for the likes of **1mm** as well - again, under 4 chars in length.
I guess a little baby table would suffice. Gee, it's fun !!! 
I already planned one to hold the BLOB jpg images of the parts - medium blob, large blob (Sounds like a 1960's 'B' movie - lol) 
An excellent PHP image manipulation suite can be found here, should anyone care to take a look.

[http://trac.gxdlabs.com/projects/phpthumb/wiki/Docs/BasicUsage](http://trac.gxdlabs.com/projects/phpthumb/wiki/Docs/BasicUsage)

I've previously looked at 'lighthouse', I think it is, but people seem to have had problems with it - I couldn't get it to work properly for me when I was playing with osCommerce a while ago.

Can't get my global arrays to work - so I'm off using the PHP POST function so kindly shown by this tutorial .... Very useful little beast...

[http://www.zend.com/zend/spotlight/mimocsumissions.php](http://www.zend.com/zend/spotlight/mimocsumissions.php)

By the time it's all done - It'll be a nice, safe, little collection of modules - By crikey I've learnt so much, both about MySql and Array handling in PHP. I can see why those 'in the know' charge so much money ;-)

As always, thanks loads for your hints, tips and suggestions.

Regards,

Phill.

P.S. - I have noted that it was suggested possibly using > SELECT * from $table with ID = $result [count][ID]  In my display.php module
with $result only holding the ID's as opposed to my populating it with all the fields I wish to display using the for / next loop. Has any one done a speed comparison on the two methods,
or is that something for me to try out sometime ?

P.P.S. - Gave up with POST example, I may return to it .. I've used implode / explode with just the ID's now ... limits me to 1024 chars (about 200 records - but, that should be more than enough !!)

---

### Post by phillw on 2009-09-18
As I am now into the finer esoterics of programming the search engine, I'd just like to finish off with saying a couple of things.

Thanks to all who have answered, chipped in, etc. I have learnt so, so much in the short time this thread has been going.

For those people ....
 
[http://www.vpolink.com/blog.php?b=26](http://www.vpolink.com/blog.php?b=26)

I have it running with what I *think* is paramatised thingies what-u-call its to get round the inches an millimeters - they are on  vertical select, scrolling little lists that return to me the 'clean' bit to go search for.

I learnt how to re-build my fulltext index (MySql doesn't like you adding a new column in the middle of its fulltext index) :)

I'm just waiting for the MySQL db to be set up on my hosting site & I'll let you all pop on and break it for me - I've tried the limited stuff i know, such as changing stuff in the URL bar and re-submitting it - darn thing is not having any of it.... I even tried to trick it into a divide by zero :lolflag:

I am GOING to have to work out how to look-up **oil** or **cap** - My current thinking is that if, after exploding the query, if I do not have a word of 4 characters long, then I'm going to have bite the bullet & do a LIKE **%oil%** in Description.

But, going back on thread - it can correctly pull up a bolt of 3/8" X 50mm  if it is asked :popcorn:

My Dad *conviently* pointed out to me that I am going to have to go to 1/64" measurements....
I'm gald I allowed 20 characters for text ==> decimal conversion field 1/64" = 0.015625   OMG !!! 
Daftly enough, it's not a problem to the db :)

Thanks to everyone who has helped & a special thanks to the person who has helped me get my head round things.

Phill.

---

### Post by phillw on 2009-10-09
Hi Bob, LTNS - Been busy with frankenstiens monster .... Anyways ... with a little bit of fulltext, a little bit of paramtised searches and a little bit of column searches for when everything else fails...it's about to be un-leashed upon an un-suspecting world.

Thanks to everyone on this thread.. The pesky critter is in debug mode (so you can see how it handles search queries).

If you'd like to see which bit you all contributed to, the parts lists you can 'play' with are 

 Ignition and Door Lock Keys, Malleable Iron Fittings, Flexible Rubber Mountings, Oils and Lubricants, Pin Spanners, Stihl TS400, Partner K650/K700, and Dolmar DPC6400.
 
Go give it some trials - I tried "the cat sat on the mat" - just out of pure devilment as i knew it would have to try and make a query up as none were 4 characters long, but all were three, which was my catchment.
it even handled "that cat sat on the other mat" and went into fulltext search

Anyways, the link is here - let me know how it behaves - it even does realmysqlescape checks on my papramtised stuff - you have all made me paranoid - lol

[http://mgjuddltd.co.uk](http://mgjuddltd.co.uk) Go to the bottom left of the buttons and you can turn 'debug' mode on - I will always leave that function there for anyone who follows this thread and wants to see how it handles things.

Once again,
thanks everyone

Phill.

---

### Post by Jive Turkey on 2009-10-12
In the future you should put your foot down and demand that they switch to the metric system.

---

### Post by phillw on 2009-10-12
> **Jive Turkey said:**
> In the future you should put your foot down and demand that they switch to the metric system.

And the engineers will just go else where .... The customer is King - forget that at your peril :)

I think inches, ounces, gallons etc. will be around for a few years yet !!

Besides, it gave a reason to make the paramatised entry section for the search.

Phill.

---

