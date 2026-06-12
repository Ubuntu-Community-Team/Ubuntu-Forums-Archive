---
title: "is there anything like speed dial in opera for firefox?"
date: 2008-08-11
forum: The Cafe
---

### Post by wolfen69 on 2008-08-11
i tried something like speed dial for firefox a while back, but it was slow as hell. anyone know of something that works good?

---

### Post by koji042 on 2008-08-11
Speed dial was one of my favorite parts of Opera. :)
In firefox, I use the Speed Dial add-on ([https://addons.mozilla.org/en-US/firefox/addon/4810]("https://addons.mozilla.org/en-US/firefox/addon/4810")). There is also another add-on called Fast Dial that works in a similar way([https://addons.mozilla.org/en-US/firefox/addon/5721]("https://addons.mozilla.org/en-US/firefox/addon/5721")).

Hope that helps.

---

### Post by cardinals_fan on 2008-08-11
Some quick html does it fine.  Here's mine:
```
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<html> <head>
<title>Speeddial</title>
</head>

<body>
<h1></h1>



<table align="center">
<tr>
  <td colspan="3" align="center">

<form method="get" action="http://www.google.com/search">
  <input type="text"   name="q" size="31"
 maxlength="255" value="" />
<input type="submit" value="Google Search" />
 </form>
    </td>
  </tr>
  <tr>
    <td><input type="button" value="Google Calendar"
onClick="window.location='http://www.google.com/calendar/render'" style="width:
180; height: 100"></td>
<td><input type="button" value="Gmail"
onClick="window.location='http://www.gmail.com/'" style="width:
180; height: 100"></td>
<td><input type="button" value="BBC"
onClick="window.location='http://news.bbc.co.uk/'" style="width:
180; height: 100"></td>
    </tr>
 <tr>
    <td><input type="button" value="Ubuntu Forums"
onClick="window.location='http://ubuntuforums.org/'" style="width:
180; height: 100"></td>
<td><input type="button" value="FeedBucket"
onClick="window.location='http://www.feedbucket.com/'" style="width:
180; height: 100"></td>
<td><input type="button" value="Arch Linux"
onClick="window.location='http://www.archlinux.org/'" style="width:
180; height: 100"></td>
    </tr>
     <tr>
    <td><input type="button" value="NetBSD"
onClick="window.location='http://www.netbsd.org/'" style="width:
180; height: 100"></td>
<td><input type="button" value="Random Stuff"
onClick="window.location='http://colonelcrayon.wordpress.com/'" style="width:
180; height: 100"></td>
<td><input type="button" value="Wikimedia"
onClick="window.location='http://www.wikimedia.org/'" style="width:
180; height: 100"></td>
    </tr>
    </table>
    
</body> </html>

```

---

### Post by binbash on 2008-08-11
there is an addon exactly for this at firefox addon site : )

---

### Post by cardinals_fan on 2008-08-11
> **binbash said:**
> there is an addon exactly for this at firefox addon site : )
I think wolfen69 already tried that and found it slow...

---

### Post by Canis familiaris on 2008-08-11
> **cardinals_fan said:**
> Some quick html does it fine.  Here's mine:
```
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<html> <head>
<title>Speeddial</title>
</head>

<body>
<h1></h1>



<table align="center">
<tr>
  <td colspan="3" align="center">

<form method="get" action="http://www.google.com/search">
  <input type="text"   name="q" size="31"
 maxlength="255" value="" />
<input type="submit" value="Google Search" />
 </form>
    </td>
  </tr>
  <tr>
    <td><input type="button" value="Google Calendar"
onClick="window.location='http://www.google.com/calendar/render'" style="width:
180; height: 100"></td>
<td><input type="button" value="Gmail"
onClick="window.location='http://www.gmail.com/'" style="width:
180; height: 100"></td>
<td><input type="button" value="BBC"
onClick="window.location='http://news.bbc.co.uk/'" style="width:
180; height: 100"></td>
    </tr>
 <tr>
    <td><input type="button" value="Ubuntu Forums"
onClick="window.location='http://ubuntuforums.org/'" style="width:
180; height: 100"></td>
<td><input type="button" value="FeedBucket"
onClick="window.location='http://www.feedbucket.com/'" style="width:
180; height: 100"></td>
<td><input type="button" value="Arch Linux"
onClick="window.location='http://www.archlinux.org/'" style="width:
180; height: 100"></td>
    </tr>
     <tr>
    <td><input type="button" value="NetBSD"
onClick="window.location='http://www.netbsd.org/'" style="width:
180; height: 100"></td>
<td><input type="button" value="Random Stuff"
onClick="window.location='http://colonelcrayon.wordpress.com/'" style="width:
180; height: 100"></td>
<td><input type="button" value="Wikimedia"
onClick="window.location='http://www.wikimedia.org/'" style="width:
180; height: 100"></td>
    </tr>
    </table>
    
</body> </html>

```

Nice Job.

---

### Post by cardinals_fan on 2008-08-11
> **Anurag_panda said:**
> Nice Job.
Thank you :)

I saw someone somewhere say that they did it that way, so I messed around a little and ended up with that.  The Google search was grabbed from someone else's code and melded into mine.

---

### Post by wolfen69 on 2008-08-11
thanks koji, fast dial is exactly what i need. it's probably even better than opera's version. a really nice addon.

---

