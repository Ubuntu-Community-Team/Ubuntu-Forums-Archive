---
title: "About to build a Media Center PC -- any suggestions?"
date: 2008-04-17
forum: The Cafe
---

### Post by st0n3cutt3r on 2008-04-17
[https://secure.newegg.com/NewVersion/Wishlist/PublicWishDetail.asp?WishListNumber=6076314&WishListTitle=Media+Center](https://secure.newegg.com/NewVersion/Wishlist/PublicWishDetail.asp?WishListNumber=6076314&WishListTitle=Media+Center)

I gave up on buying a s939 mATX board to recycle my hardware with, but I still want a media center that I can also use as a web server.

things I'm looking for are: [LIST]
[*]**Composite output** (I don't have an HDMI display... yet)
[*]Cost (cheaper is better)
[*]Dual-core (I don't want any lag while watching movies / hosting content)
[*]Compatible with ubuntu (I'm not going to cry if I have to use windows or something else; I would just prefer to be on ubuntu)
[*]Form/Size (a case that isn't an eyesore is a huge perk, and a smaller case is easier to find places for in general)
[*]Internal Wifi (I don't want an adaptor for wifi hanging out... it's too much of a risk to break off or disconnect by mistake)
[/LIST]

I already have a HDD, and an Optical drive, and I'm open to suggestions so long as composite video output is available (I don't mind using an adaptor, as long as I can find a suitable one)

What suggestions do you have?

---

### Post by -gabe-noob- on 2008-04-17
If you dont want to build there are great PC's at low prices at 

[http://www.zareason.com/shop/home.php](http://www.zareason.com/shop/home.php) with ubuntu pre-installed and they have a media center one, also checkout their warenty, It doesn't void when you modify your pc.

---

### Post by herbster on 2008-04-17
I just did this exact "project" about a week ago. I built a new rig a couple months ago and had to RMA the old vid card and hd, so I was investigating my options while I waited for 'em. My server's parts are:

Asus P4V8X-MX
P4 3.4ghz EE (HT)
1.2gb ram
500gb hd
7600GS 512
Lite-On DVD-RW
Hauppauge PVR-150 w/remote (has composite)

The most important thing here is to get a good PSU [+case]. I grabbed the Antec NSK4480B, comes with a 380w 80% PSU, well built. If you're going to have a lot of data sitting on the sucker you would be unwise to cut any costs with the PSU/case so it runs at good temps as well.

I installed Arch on the server (you will probably install Ubuntu), and MythTV. If you are unfamiliar with Myth, check mythtv.org. MythTV works with backends/frontends. The backend being the "server" that does all the activity for recording, capturing, sorting the video content, allowing any networked machine to be a frontend (ie., to connect to the backend and view content).

I basically have the mythbackend running, along with ktorrent which has a fantastic little HTML plugin so you can control parts of it from a browser on a networked machine, and I set up NFS for file sharing, so my server share where everything goes is easily accessible on my desktop box. And there is never any lag from the server it's more than fast enough to handle all of it.

You really don't need dual-core for a server, but what is your budget? You state cheaper is better, so it will depend on how much you're willing/able to spend altogether/per part. ie., For dual-core and a wifi-ready mobo, that ain't coming "cheap."

---

