---
title: "Certain websites on my University internet network have been blocked"
date: 2008-09-25
forum: Security
---

### Post by Dr.Suave on 2008-09-25
It's not how it sounds!

Basically, since connecting my laptop to my Uni's network, I haven't been able to download any .torrent files. The download always fails, and sometimes I get a message (it's unclear who this message is from) saying something about a high security risk and that I'm not allowed to access this "website".

I'm not going to download a virus through bit torrent, and the program can be used for perfectly legitimate reasons (like downloading Ubuntu faster).

Does anyone have any idea how to get around this block? I'm willing to use an encryption program if anyone has any good ones, but would prefer a simpler method if possible.

Thanks!
Wilf

---

### Post by anotherdisciple on 2008-09-25
Bypassing your University's security is against the law. You could get kicked out of school for this.


Just kidding... I just wanted to be the first person to give you a lecture that you didn't want to hear. I don't know how to get around it though.

---

### Post by oldsoundguy on 2008-09-25
> **Dr.Suave said:**
> 

I'm not going to download a virus through bit torrent, and the program can be used for perfectly legitimate reasons (like downloading Ubuntu faster).

Wilf


Sorry, but you CAN download a virus or all sorts of malware via a torrent on an unprotected system.  Especially Warze or cracks or key gen's!

It is your university's ball, ballpark, ballgame and rules.

Some do not want FILE SHARING of any kind (it DOES clog up the system)  and torrents are just that as you are uploading at the same time you are downloading .. takes more bandwidth.

Too bad there is no distinction between legit downloads and blatant copyrighted file sharing.  But at present, there is none.

---

### Post by Nepherte on 2008-09-25
If it's against the usage agreement of your university network, then you will have to cope with that. A lot of universities, if not all, do this because peer 2 peer protocols generate a lot of network traffic. If every student would be using those protocols, the network is incapable of handling the traffic.

---

### Post by DrMega on 2008-09-25
Many companies and such restrict certain sites. At my work they use some piece of software running on the proxy servers to limit access. There are ways round it (sometimes) but surely it is best to just accept the wishes of the admins rather than risk getting kicked out of uni (or fired from your job).

Torrents will be restricted probably as much for the legal implications as much as any other reason. If you were to download a pirated DVD iso at uni (I'm not suggesting you would, but you could if you could use torrents), and someone as going to get done, it would be the university that would liable by default, unless they could prove it was you. Either way it would be a real headache for the university, so it is better for them to just impose a blanket ban on downloads of that nature.

It is also worth noting that the ISP may have imposed the restriction rather than the university. In the UK the big four ISPs have all implemented restrictions on certain ports to try to curb torrent downloads.

---

### Post by Dr.Suave on 2008-09-25
Blimey, I was brought to justice by a ninja, and then the general public!

Obviously, I don't expect anyone to help me do anything they think is immoral. I may not agree with you, just as you don't agree with me, but I'm not going to get arsey with anyone.

Just out of interest though (and this really is just out of interest, I'm not trying to convince any of you to change your minds), do you think that the same arguments should be used to stop me from recieving my post, as the mail can be used for the illegal distribution of not just copywrited software and music, but also drugs and weapons, and so obviously poses a much more serious threat to my University?

Thanks for reading and whatnot

Wilf

---

### Post by DrMega on 2008-09-25
> **Dr.Suave said:**
>  do you think that the same arguments should be used to stop me from recieving my post, as the mail can be used for the illegal distribution of not just copywrited software and music, but also drugs and weapons, and so obviously poses a much more serious threat to my University?

It's not anyone here that's trying to stop you, its not a matter of changing anyones minds, its either the uni or the isp.

I guess the issue is that it is far more common to transmit dodgey stuff electronically than physically. People download pirated material all the time, but I guess its less common that pirated stuff gets shipped about in the post.

If you have a genuine case to download a specific torrent, have a word with the network admins. They *might* unblock that file or let you have temporary access to a machine that connects to a less restricted proxy server.

---

### Post by redgsturbo on 2008-09-25
If you just want to download stuff faster, get a multiconnection program (I use axel)  If you are honestly wanting torrent access, you have to bypass whatever they are doing.... that can be done a number of ways, but you need to figure out exactly how they are blocking your traffic.  Also, breaking their policy means assuming the risks involved, whatever they may be

---

### Post by cdenley on 2008-09-25
I'm kind of curious about how it is being blocked. Is it an entire website you can't access?
```

host blockedsite.com
wget -O /dev/null http://blockedsite.com/

```

---

### Post by sloggerkhan on 2008-09-25
oops.... must be weird browser lag causing a double post.

---

### Post by sloggerkhan on 2008-09-25
He didn't ask for a lecture. So don't give one, people.

If it's the torrent file itself that you can't access, or webpages which host them, it is likely that you university is somehow inspecting traffic in between you and that website, or has a list of blocked sites. You need to establish a secure/encrypted connection to either that website or a proxy site of some kind in order to download the .torrent file.

If it's the torrent itself you are having trouble with, use a client like deluge and force full stream encryption.

---

### Post by Nepherte on 2008-09-25
I don't have the feeling that anyone is lecturing the topic starter. Some people just don't want to aid people in breaking a university's policy. I don't think the encrypt traffic option in Deluge will bypass it but as you said, it's possible with some method x.

---

### Post by redgsturbo on 2008-09-25
stunnel is good for tunneling any tcp over ssl..

it could be as simple as them blocking any url that has 'torrent' in it, or dealing you a crap DNS response, or they could be analyzing http traffic to see if its really web traffic or p2p (maybe, but this is expensive)... if the latter, try MSE/PE which encrypts bt traffic and makes it more difficult to distinguish from regular http... failing THAT, you can tor the tracker traffic though tor really isn't made for that, failing THAT, setup an ssh tunnel to your home, and push your stuff through that

---

### Post by Dr.Suave on 2008-09-25
It's just the torrent file, everything else seems to be fine.

I get this message when I try to download them from mininova.org:

> High security alert!!!

You are not permitted to download the file "Let it Bleed [mininova].torrent".

URL = [http://www.mininova.org/get/1826586](http://www.mininova.org/get/1826586)

cdenley:

I get this from your command:

```
wilf@ubuntu-laptop:~$ wget -O /dev/null http://www.mininova.org/get/1826586
--21:55:05--  http://www.mininova.org/get/1826586
           => `/dev/null'
Resolving www.mininova.org... 87.233.147.140
Connecting to www.mininova.org|87.233.147.140|:80... connected.
HTTP request sent, awaiting response... 200 Ok
Length: unspecified [text/html]

    [ <=>                                         ] 197           --.--K/s
```

I'm not sure, but that looks like it managed to download the page which refers me to the torrent URL, but not the torrent itself.

Thanks for the help guys.

Does anyone reckon something like Tor might help?

Even if it's not for this kind of thing, installing Tor might be a good idea anyway, as I'm on a public network.

Wilf

---

### Post by Dr.Suave on 2008-09-25
redgsturbo: I think they're blocking any URL that ends in .torrent

thats mostly a guess though

---

### Post by oldsoundguy on 2008-09-25
the easiest way around the torrent blockage issue is to sign up for universal internet such as is advertised on the toob and use a plug in card/dongle and GO WIRELESS.  It will, however, COST you vs the FREE service you get now as a student/faculty member of the university.

Add this to why they can darn well do as they please as far as restricting usage .... the service is FREE to authorized people.

If they say, no .. darn good chance they mean it!

(and breaking their rules can, at least, get you even MORE restrictions as to usage piled on .. even so far as to deny you service!  THEIR RULES!)

---

### Post by redgsturbo on 2008-09-25
> **Dr.Suave said:**
> It's just the torrent file, everything else seems to be fine.

I get this message when I try to download them from mininova.org:



cdenley:

I get this from your command:

```
wilf@ubuntu-laptop:~$ wget -O /dev/null http://www.mininova.org/get/1826586
--21:55:05--  http://www.mininova.org/get/1826586
           => `/dev/null'
Resolving www.mininova.org... 87.233.147.140
Connecting to www.mininova.org|87.233.147.140|:80... connected.
HTTP request sent, awaiting response... 200 Ok
Length: unspecified [text/html]

    [ <=>                                         ] 197           --.--K/s
```

I'm not sure, but that looks like it managed to download the page which refers me to the torrent URL, but not the torrent itself.

Thanks for the help guys.

Does anyone reckon something like Tor might help?

Even if it's not for this kind of thing, installing Tor might be a good idea anyway, as I'm on a public network.

Wilf

getting the torrent file through tor is fine, but actually running bt through tor is poor form

---

### Post by cdenley on 2008-09-25
> **Dr.Suave said:**
> It's just the torrent file, everything else seems to be fine.

I get this message when I try to download them from mininova.org:



cdenley:

I get this from your command:

```
wilf@ubuntu-laptop:~$ wget -O /dev/null http://www.mininova.org/get/1826586
--21:55:05--  http://www.mininova.org/get/1826586
           => `/dev/null'
Resolving www.mininova.org... 87.233.147.140
Connecting to www.mininova.org|87.233.147.140|:80... connected.
HTTP request sent, awaiting response... 200 Ok
Length: unspecified [text/html]

    [ <=>                                         ] 197           --.--K/s
```

I'm not sure, but that looks like it managed to download the page which refers me to the torrent URL, but not the torrent itself.

Thanks for the help guys.

Does anyone reckon something like Tor might help?

Even if it's not for this kind of thing, installing Tor might be a good idea anyway, as I'm on a public network.

Wilf

It appears they are blocking http requests for certain filenames. Tor slows your internet down to a crawl. If I were you, I would use tor with something like torbutton, then turn on tor to save torrents, then hopefully the torrent will work on your network once retrieved.

I think using tor for casual web browsing is a bad idea.
[http://ubuntuforums.org/showpost.php?p=5852951&postcount=6](http://ubuntuforums.org/showpost.php?p=5852951&postcount=6)

---

### Post by Dr.Suave on 2008-09-25
Thanks for all the help everyone, it's much appreciated. This obviously pushed a few buttons, so I'll just say that at this point it's just a consideration, and there are alternative ways of downloading stuff which the administrator doesn't seem bothered about (like redgsturbo's multiconnection suggestion).

Thanks again,

Wilf

---

### Post by lisati on 2008-09-25
It's always good to keep on friendly terms with the university or ISP who could pull the plug - if you have to be "sneaky" while using their services, it's often a sign that there's a problem somewhere: don't be scared to work with them rather than behind their back.

---

### Post by sloggerkhan on 2008-09-25
So an encrypted connection to a proxy didn't work for downloading the torrent?

---

### Post by Dr.Suave on 2008-09-26
Sloggerkhan: Actually, there's been so much moral input that I haven't tried it yet! I think that using Torbutton to download the .torrent file itself and then using deluge with full encryption will do the trick.

But there have been some pretty valid points against the whole thing, the best one being that I might slow the network down pretty badly, might be a bit harsh on all the other users.

It might be the kind of thing best left as a last resort, and only done at a time when no one will be using the network.

I did open Azureus to see if any of my uploading torrents were getting through successfully, and nothing was getting out, so it looks like they have some clever security.

---

### Post by mikewhatever on 2008-09-26
Apart from moral input, about which you don't seem to care much, do consider your own good and well being. You can get suspended for downloading stuff from mininova using your university network. Do you want to graduate at all?

---

### Post by Joeb454 on 2008-09-26
Thread Closed. Bypassing your University's Internet restrictions isn't something we support here.

I suggest you ask your University's Network Admin's :)

---

