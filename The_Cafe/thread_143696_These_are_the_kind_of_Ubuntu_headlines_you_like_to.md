---
title: "These are the kind of Ubuntu headlines you like to see"
date: 2006-03-12
forum: The Cafe
---

### Post by matthew on 2006-03-12
From digg.com, click for link

[Ubuntu Password Bug Fixed In Just A Few Hours]("http://digg.com/linux_unix/Ubuntu_password_bug_fixed_in_just_a_few_hours")

---

### Post by bjweeks on 2006-03-12
[http://digg.com/linux_unix/Administrator_root_password_readable_in_cleartext_on_Ubuntu_Breezy](http://digg.com/linux_unix/Administrator_root_password_readable_in_cleartext_on_Ubuntu_Breezy) :rolleyes:

---

### Post by matthew on 2006-03-12
[quote=bjweeks][http://digg.com/linux_unix/Administrator_root_password_readable_in_cleartext_on_Ubuntu_Breezy]("http://digg.com/linux_unix/Administrator_root_password_readable_in_cleartext_on_Ubuntu_Breezy") :rolleyes:[/quote]Yeah, that's the one that's been fixed. :)

---

### Post by bjweeks on 2006-03-12
I know... I read that earlier and then went to check the forums and saw a new USN. I was like wow fast then go check digg again and that is on the homepage...

---

### Post by matthew on 2006-03-12
[quote=bjweeks]I know... I read that earlier and then went to check the forums and saw a new USN. I was like wow fast then go check digg again and that is on the homepage...[/quote]Very cool. Super huge props to the Ubuntu dev team!!

---

### Post by mstlyevil on 2006-03-12
Lets see Apple or MSFT do that.

---

### Post by ssam on 2006-03-13
[QUOTE=matthew]From digg.com, click for link

[Ubuntu Password Bug Fixed In Just A Few Hours]("http://digg.com/linux_unix/Ubuntu_password_bug_fixed_in_just_a_few_hours")[/QUOTE]

thank you :-)

now why are people making out that this was the worst bug ever?
its not a remote exploit
it does not effect every user
only a problem if you have not changed the password since install
etc

is there a known case of anyone being bitten yet?

---

### Post by bjweeks on 2006-03-13
> its not a remote exploit

Yes it is. If somebody gets a user ssh account they can now get root.

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]Yes it is. If somebody gets a user ssh account they can now get root.[/QUOTE]

No it's not, as it still requires a local account. That it's obviously possible to access local accounts remotely doesn't change this.

According to your definition there wouldn't be any destinction between local and remote exploits, though there of course clearly is.

Anyway, if your point was that people shouldn't easily dismiss vulnerabilities like this because they are "only" local, I agree with you.

P.S.: Sorry for dropping in, but I just had to comment on this, as it was so blatantly false.

---

### Post by bjweeks on 2006-03-13
[QUOTE=bugmenot]No it's not, as it still requires a local account. That it's obviously possible to access local accounts remotely doesn't change this.

According to your definition there wouldn't be any destinction between local and remote exploits, though there of course clearly is.

Anyway, if your point was that people shouldn't easily dismiss vulnerabilities like this because they are "only" local, I agree with you.

P.S.: Sorry for dropping in, but I just had to comment on this, as it was so blatantly false.[/QUOTE]

It can be exploited remotely therefore it is a remote exploit.

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]It can be exploited remotely therefore it is a remote exploit.[/QUOTE]
No it isn't.
According to your definition, every exploit would be a remote exploit. While this is technically true, as everything on a computer can be accessed remotely, if the computer is configured this way, it's still non-sensical, as there clearly is a distinction between exploits that need a local account and exploits that don't need one.

Why you insist on ignoring this distinction is beyond me.

---

### Post by Jussi Kukkonen on 2006-03-13
[QUOTE=matthew]
These are the kind of Ubuntu headlines you like to see
[/QUOTE]

Well... It's nice they fixed it fast. But frankly, this was the worst security blunder in a long time, on any OS:
[LIST]
[*]The passwords have been lying there user-readable for months on thousands of computers
[*]This is quite easy to notice, and we've been very lucky if no black hats haven't already used this. If this had happened on a more server oriented distro, the consequences would have been catastrofic...
[/LIST]
One more reason to like console-installers -- it can run straight *passwd* and not resort to saving the password to a file (just for a while!)...

---

### Post by bjweeks on 2006-03-13
[QUOTE=bugmenot]No it isn't.
According to your definition, every exploit would be a remote exploit. While this is technically true, as everything on a computer can be accessed remotely, if the computer is configured this way, it's still non-sensical, as there clearly is a distinction between exploits that need a local account and exploits that don't need one.

Why you insist on ignoring this distinction is beyond me.[/QUOTE]

So I run a server and give people accounts, one remotely uses this expolit to get root. How is this in any way local?

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]So I run a server and give people accounts, one remotely uses this expolit to get root. How is this in any way local?[/QUOTE]
Because you had to give the people a local account before.

As I said, according to your definition, everything is a remote exploit, as theoretically any function of a computer can also be done remotely, if the computer is configured accordingly.

This however does not take into account that there is a distinction between exploits that need a local account and exploits that don't.

I'll ask you again, why you insist on ignoring this distinction.

Do you really think it makes no difference if an exploit needs a local account, or if it doesn't? Is this what you are trying to tell us?

Edit: And while we are at it.
According to you, are there any local exploits?
If there are, what makes them local, if there aren't, why should it make sense not to make a distinction between exploits that need a local user account and exploits that don't?

---

### Post by bjweeks on 2006-03-13
[QUOTE=bugmenot]Because you had to give the people a local account before.

As I said, according to your definition, everything is a remote exploit, as theoretically any function of a computer can also be done remotely, if the computer is configured accordingly.

This however does not take into account that there is a distinction between exploits that need a local account and exploits that don't.

I'll ask you again, why you insist on ignoring this distinction.

Do you really think it makes no difference if an exploit needs a local account, or if it doesn't? Is this what you are trying to tell us?

Edit: And while we are at it.
According to you, are there any local exploits?
If there are, what makes them local, if there aren't, why should it make sense not to make a distinction between exploits that need a local user account and exploits that don't?[/QUOTE]

Or the server could be running a ftp server and a user could see that log.

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]Or the server could be running a ftp server and a user could see that log.[/QUOTE]
No, unless of course the admin of the ftp server really made great pains to make his setup as insecure as humanly possible.

Anyway, how about answering one of my questions, or are you content with making false claims, like with the ftp server and ignoring the points I make?
Because if this is the case, I'm clearly wasting my time.

---

### Post by bjweeks on 2006-03-13
This could be expolited in MANY ways and does NOT need a local account.

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]This could be expolited in MANY ways and does NOT need a local account.[/QUOTE]
????
Still not answering my questions, I see.
Also, changing out tune about what this is all about, aren't we?
But just out of curiosity, how could this be exploited without having a local account?
And can I construe your sentence to mean that you agree with me that there is a clear distinction between exploits that need a local account and those that don't?
And if that is the case, would you agree that not calling exploits that need a local account remote exploits makes sense?

---

### Post by bugmenot on 2006-03-13
ROFL at this being a bugmenot account...

If somebody gets the log they get root. No account needed.

---

### Post by PatrickMay16 on 2006-03-13
It's good that a patch was released straight away, but you can't deny that this was a pretty big mistake.

---

### Post by Jucato on 2006-03-13
[QUOTE=Jussi Kukkonen]Well... It's nice they fixed it fast. But frankly, this was the worst security blunder in a long time, on any OS:
[LIST]
[*]The passwords have been lying there user-readable for months on thousands of computers
[*]This is quite easy to notice, and we've been very lucky if no black hats haven't already used this. If this had happened on a more server oriented distro, the consequences would have been catastrofic...
[/LIST]
One more reason to like console-installers -- it can run straight *passwd* and not resort to saving the password to a file (just for a while!)...[/QUOTE]

I wouldn't go so far as calling it the worst security blunder in a long time.
1. If you've read the report in the Security section of the forums, this bug is only present in Breezy. Not in Hoary, not in Dapper. as Breezy was released October 2005, the bug has only been alive for 5 months or less. Compare that to a design flaw that has been present for years, like the WMF flaw. Now THAT is something that was lucky not to have been exploited sooner.
2. The log file only includes the password that was made during the installation. If the password has been changed after that, it is not recorded.
3. The password in the file is quite easy to notice. But the file itself is not. It's located 4 directories deep.

But still, it is a very critical bug, especially once word got out. That's why the devs responded quickly. That is one of the things that people are praising. Faced with an equally threatening (perhaps even greater, considering Windows' widespread use, etc) bug, Microsoft did not respond as promptly as they should have. Perhaps not within a few hours, but not even in a few days.

EDIT: Just wanted to link to the Security section and post the quote:
[http://ubuntuforums.org/showthread.php?t=143622]("http://ubuntuforums.org/showthread.php?t=143622")
> This does not affect the Ubuntu 4.10, 5.04, or the upcoming 6.04  installer. However, if you upgraded from Ubuntu 5.10 to the current development version of Ubuntu 6.04 ('Dapper Drake'), please ensure that you upgrade the passwd package to version 1:4.0.13-7ubuntu2 to fix the installer log files.

---

### Post by Klaidas on 2006-03-13
It'd be cool if Slashdot posted this big fixing :)
On the other hand, forums could get  [slashdotted]("http://en.wikipedia.org/wiki/Slashdotted") :/

---

### Post by bugmenot on 2006-03-13
[QUOTE=bugmenot]ROFL at this being a bugmenot account...

If somebody gets the log they get root. No account needed.[/QUOTE]
But an other vulnerability that enables them to get the log. ;)

---

### Post by bjweeks on 2006-03-13
[QUOTE=bugmenot]But an other vulnerability that enables them to get the log. ;)[/QUOTE]

or stupidity or social engineering.

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]or stupidity or social engineering.[/QUOTE]
Which are pretty much the same as a vulnerability.

Anyway, how about answering one of my questions, or are you going to point out next that everything is vulnerable anyway, as the admin could just post the root password in plain text on the internet?

Just to make sure you forgot it, we were discussing your point:
> It can be exploited remotely therefore it is a remote exploit.

And I asked you these questions about it, which you steadfastly refuse to answer:
> I'll ask you again, why you insist on ignoring this distinction.

Do you really think it makes no difference if an exploit needs a local account, or if it doesn't? Is this what you are trying to tell us?

Edit: And while we are at it.
According to you, are there any local exploits?
If there are, what makes them local, if there aren't, why should it make sense not to make a distinction between exploits that need a local user account and exploits that don't?

Still not answering my questions, I see.
Also, changing out tune about what this is all about, aren't we?
But just out of curiosity, how could this be exploited without having a local account?
And can I construe your sentence to mean that you agree with me that there is a clear distinction between exploits that need a local account and those that don't?
And if that is the case, would you agree that not calling exploits that need a local account remote exploits makes sense?


---

### Post by bjweeks on 2006-03-13
> Do you really think it makes no difference if an exploit needs a local account, or if it doesn't? Is this what you are trying to tell us?

Sure is does but this is not the case as if you can get the log you don't need a user account.

> According to you, are there any local exploits?

A exploit that can't be exploited remotely is a local exploit(eg. biso exploit or a exploit that can only be used at the pc itself).

> But just out of curiosity, how could this be exploited without having a local account?

There is a endless ways of getting the log file.

> And if that is the case, would you agree that not calling exploits that need a local account remote exploits makes sense?

See above.

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]Sure is does but this is not the case as if you can get the log you don't need a user account.
[/quote]
Jesus...
Your original post to with I reacted was arguing that something is a remote exploit, if the following were the case: "If somebody gets a user ssh account they can now get root.".

I pointed out about a hundred times now that this was wrong and claiming that you can get the log file an other way does no change your initial claim and my arguments against it.

[QUOTE=bjweeks]
A exploit that can't be exploited remotely is a local exploit(eg. biso exploit or a exploit that can only be used at the pc itself).
[/quote]
Ehm, but as I already pointed out, practically everything you can do locally can also be done remotely, so your point is? And could you give a concrete example of something you consider a local exploit?

[QUOTE=bjweeks]
There is a endless ways of getting the log file.
[/quote]
No, there isn't.
The only viable ways are having a local account, or having an other kind of vulnerability, that allows unauthorized people to see this lock file.
But again, this is totally irrelevant to your initial claim. (If somone with an ssh account can use it, it's a remote exploit.

Oh and see above is not an answer to:
And if that is the case, would you agree that not calling exploits that need a local account remote exploits makes sense?

---

### Post by bjweeks on 2006-03-13
Fine, my "initial claim" was wrong and my claim now is still valid. If somebody gets the log file this becomes a remote exploit.

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]Fine, my "initial claim" was wrong and my claim now is still valid. If somebody gets the log file this becomes a remote exploit.[/QUOTE]
Oh come on, what are you trying to tell us?
That if someone gets the root password in plain text, it's a serious issue?
Nobody disputed that.

Note though that you still need some way to log into the computer (that is most probably an ssh daemon running) to use a root password that you have to attack the computer remotely.

---

### Post by bjweeks on 2006-03-13
Just cause you need to run ssh for the expolit to work does not make it any less of a exploit.

---

### Post by megamania on 2006-03-13
[QUOTE=bjweeks]Fine, my "initial claim" was wrong and my claim now is still valid. If somebody gets the log file this becomes a remote exploit.[/QUOTE]

And please, **bugmenot**, stop being controversial otherwise you're not coming to my birthday partyyyyyy.  ;-)

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]Just cause you need to run ssh for the expolit to work does not make it any less of a exploit.[/QUOTE]
It does, for all the people not running ssh for example.

And having the root password is not an exploit anyway, as the exploit is getting the root passward in the first place, so saying that having the root password == a remote exploit doesn't make any sense in the first place.

---

### Post by bjweeks on 2006-03-13
Um it's a exploit cause IT STORES THE ROOT PASSWORD IN A FILE!

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]Um it's a exploit cause IT STORES THE ROOT PASSWORD IN A FILE![/QUOTE]
No, the exploit is getting the file and hence the password in the first place. Once you have it, you already exploited the vulnerability, but you don't have an exploit, but a password.

Sorry, no birthdaypartyyy for me I guess. :cry:

---

### Post by bjweeks on 2006-03-13
[QUOTE=bugmenot]No, the exploit is getting the file and hence the password in the first place. Once you have it, you already exploited the vulnerability, but you don't have an exploit, but a password.

Sorry, no birthdaypartyyy for me I guess. :cry:[/QUOTE]

I can exploit this vulnerability by asking for somebody log. If this was not a exploit I could not get the root passowrd from the log.

---

### Post by bugmenot on 2006-03-13
[QUOTE=bjweeks]I can exploit this vulnerability by asking for somebody log.
[/quote]
Yes and nobody disputet that.

[QUOTE=bjweeks]
If this was not a exploit I could not get the root passowrd from the log.[/QUOTE]
Slight correction. If this wasn't a vulnerability.

Anyway, how does that make your claim that "If somebody gets the log file this becomes a remote exploit." valid?

As I already said, if somebody gets the logfile and hence the root password, the exploit already happened.

Finally, I really don't know what you are trying to say here. I get the impression you are just arguing for the sake of arguing.

As I already said in my first post, if you wanted to make the point that people should not shrug this of, because it is "only" a local exploit, I totally agree with you.

I'm sure you'll find that many attacks rely on a combination of remote exploits and local exploits like this one here, so people shouldn't dismiss this easily.

---

### Post by Lovechild on 2006-03-13
"Completely idiotic security hole in Ubuntu fixed at normal rate" - yes I could see that being a benefit. 

I was hoping it was a mass conversion story.

---

### Post by Kerberos on 2006-03-13
[QUOTE=Fenyx]
But still, it is a very critical bug, especially once word got out. That's why the devs responded quickly. That is one of the things that people are praising. Faced with an equally threatening (perhaps even greater, considering Windows' widespread use, etc) bug, Microsoft did not respond as promptly as they should have. Perhaps not within a few hours, but not even in a few days.
[/QUOTE]
I dont even use Linux regularly anymore, and I could write the fix for this.
```
rm /var/log/installer/cdebconf/questions.dat
```
1. Root shouldn't get written unencrypted to disk.  Ever.  Its that simple.  It just shouldn't happen.  This is a massive blunder and if MS did this I dont think this thread would be praising them for such a quick fix

2. Ubuntu has been widely distributed, many to places where there isn't net access and now anyone with an account on that system can get root on that system.  As Microsoft learned unless you actively harass the users to do security updates most of the time they don't.  This bug didn't dissapear the Sunday they patched it on.

3. The WMF vulnerability is due to a malformed WMF file (probably a buffer overflow) and it is both massively more time consuming to track down and fix (I made a fix for the Linux one, you make a fix the WMF one mmkay?) and is probably the result of a simple programmer mistake like array bounds checking as opposed to a massive, quite frankly unnaceptable, blunder, which is writing the root password to disk unencrypted!

But why not pass off massive incompetance on the behalf of some Ubuntu programmers by having a bash at Microsoft to make Ubuntu seem less insecure.  Programmers are programmers and they all make mistakes, writing 'closed source' doesn't automatically make the resulting compiled code inferior no matter how much you'd like that to be the case.

---

### Post by Leo_01 on 2006-03-13
[QUOTE=Fenyx]I wouldn't go so far as calling it the worst security blunder in a long time.
1. If you've read the report in the Security section of the forums, this bug is only present in Breezy. Not in Hoary, not in Dapper. as Breezy was released October 2005, the bug has only been alive for 5 months or less. Compare that to a design flaw that has been present for years, like the WMF flaw. Now THAT is something that was lucky not to have been exploited sooner.
2. The log file only includes the password that was made during the installation. If the password has been changed after that, it is not recorded.
3. The password in the file is quite easy to notice. But the file itself is not. It's located 4 directories deep.

But still, it is a very critical bug, especially once word got out. That's why the devs responded quickly. That is one of the things that people are praising. Faced with an equally threatening (perhaps even greater, considering Windows' widespread use, etc) bug, Microsoft did not respond as promptly as they should have. Perhaps not within a few hours, but not even in a few days.

EDIT: Just wanted to link to the Security section and post the quote:
[http://ubuntuforums.org/showthread.php?t=143622]("http://ubuntuforums.org/showthread.php?t=143622")[/QUOTE]

I guess it should not even be counted as a blunder...
ALL HUMANS MAKE MISTAKES.
It really depends on how fast the mistake is corrected.

---

### Post by Leo_01 on 2006-03-13
[QUOTE=Kerberos]I dont even use Linux regularly anymore, and I could write the fix for this.
```
rm /var/log/installer/cdebconf/questions.dat
```
1. Root shouldn't get written unencrypted to disk.  Ever.  Its that simple.  It just shouldn't happen.  This is a massive blunder and if MS did this I dont think this thread would be praising them for such a quick fix

2. Ubuntu has been widely distributed, many to places where there isn't net access and now anyone with an account on that system can get root on that system.  As Microsoft learned unless you actively harass the users to do security updates most of the time they don't.  This bug didn't dissapear the Sunday they patched it on.

3. The WMF vulnerability is due to a malformed WMF file (probably a buffer overflow) and it is both massively more time consuming to track down and fix (I made a fix for the Linux one, you make a fix the WMF one mmkay?) and is probably the result of a simple programmer mistake like array bounds checking as opposed to a massive, quite frankly unnaceptable, blunder, which is writing the root password to disk unencrypted!

But why not pass off massive incompetance on the behalf of some Ubuntu programmers by having a bash at Microsoft to make Ubuntu seem less insecure.  Programmers are programmers and they all make mistakes, writing 'closed source' doesn't automatically make the resulting compiled code inferior no matter how much you'd like that to be the case.[/QUOTE]
FYI the WMF exploit is worst!
Any graphics file can be used to take avantage of the WMF exploit.
Worst still it takes like 1 or 2 years for MS to even notice their WMF patch.
Which is worst then?

Check this out : 
> 
There are several methods of classifying exploits. The most common is by how the exploit contacts the vulnerable software. A 'remote exploit' works over a network and exploits the security vulnerability without any prior access to the vulnerable system. A 'local exploit' requires prior access to the vulnerable system and usually increases the privileges of the person running the exploit past those granted by the system administrator.

Taken from Wikipedia.

---

### Post by Kerberos on 2006-03-13
[QUOTE=Leo_01]FYI the WMF exploit is worst!
Any graphics file can be used to take avantage of the WMF exploit.
Worst still it takes like 1 or 2 years for MS to even notice their WMF patch.
Which is worst then?
[/QUOTE]
My point was the WMF flaw is quite an intricate bug, probably caused by some glitch like confusing a pointer with an array.  The Ubuntu bug otoh is caused by seriously bad programming practice - Unnecessary logging, the logging of a root password unencrypted, the resulting log being world readable, and not deleting it when its done.  This thread is praising Ubuntu for doing something that would get MS tarred and feathered, but instead 'its fine as you can get root with the WMF flaw'.  Everyone makes mistakes and this one is a particulary bad one (from a programmers point of view) and the WMF exploit has nothing to do with it.  Its not as critical a bug, but its still inexcusable and its certainly not the kind of bug I 'like to see'.

Not that I think anything needs to be done, everyone makes mistakes and I am sure that a few people learned a valuable lesson here, but making up excuses and pointing at MS and saying 'its fine because they are worse' is utterly pointless.  There is no need to defend them over this - its a huge mistake, they get made by everyone, get over it.

---

### Post by ssam on 2006-03-13
the worst kind of vunerability is one that allow somebody to break into a machine requiring only a network connection. this is generally called a remote exploit. these are a huge problem as you machine is vunerable just be being online.

the 34606 bug was basically a privilege escalation. these are fairly comon in many operating systems. still a very serious problem if you run a multiuser system. bug for a home user with a default install and only trusted users there is no real risk.

privilege escalation combined with another bug (eg, badly writen cgi) could lead to a remote exploit.

another thing that softens to impact of this bug is that it seems it did not happen on all systems. also in corprate environments passwords are changed regularly (only the install password was visable).

the bug is embarrasing because it seems like a silly mistake. [http://www.ubuntuforums.org/showpost.php?p=818037&postcount=61](http://www.ubuntuforums.org/showpost.php?p=818037&postcount=61) explains how it happened. its slightly more complex than it seems. MSSQL server and mac os x have both had bugs that make passwords visible in plain text. all programs dealing with password must atleast hold them in RAM in plain text, and if this RAM is swaped to disk then that can be a problem.

while it is worrying that this existed, and lay undetected for a long time, it is good that it was patched very promptly even on a sunday night. if all ubuntu security bugs are patched this quick we have little to worry about.

i have not yet heard of any breakins caused by this bug.

update:
secunia rate it as "less critical" see [http://secunia.com/advisories/19200/](http://secunia.com/advisories/19200/)

---

