---
title: "Building Biarch (Shared WoW64) Wine On Ubuntu"
date: 2013-09-15
forum: Virtualisation
---

### Post by Adrie_Nel on 2013-09-15
[B]Building Biarch (Shared WoW64) Wine On Ubuntu 
[SIZE=2][FONT=arial black]*[ [http://wiki.winehq.org/BuildingBiarchWineOnUbuntu](http://wiki.winehq.org/BuildingBiarchWineOnUbuntu) ]*[/FONT][/SIZE] [COLOR=#800080][SIZE=1]- you need to follow this link - [/SIZE][/COLOR][/B]

[COLOR=#ee82ee]Reason: build 32 bit wine inside a 32 bit container with LXC to use Wine32 & Wine64 together for irreplacable [yet] CAD & other programs[/COLOR]

SO:

[FONT=arial]I downloaded the newest wine 1.7 for Raring:
[/FONT][FONT=arial]git clone git://source.winehq.org/git/wine.git ~/wine-git

BUT:

[/FONT][FONT=arial][COLOR=#a52a2a]*_ONE_*
[/COLOR]
sudo apt-get build-dep wine 
[ takes me into an infinite loop: ]
"The following packages will be REMOVED:
  libsane-dev libtiff5-dev
The following NEW packages will be installed:
  libtiff4-dev
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded"
[COLOR=#ff0000]HOWEVER if I let it do this, it complains about the removed ones as missing - and the other way around, it complains about [/COLOR][/FONT][FONT=arial][COLOR=#ff0000][FONT=arial]libtiff4-dev missing [/FONT]- 
leaving me UNABLE to get out of this infinite loop...[/COLOR] 
[/FONT][FONT=arial]
So I leave the newer files installed and go on...


[COLOR=#a52a2a]*_TWO_*[/COLOR]

Definately Installed:[COLOR=#008000] build-essential[/COLOR]:
[COLOR=#0000ff]"Reading state information... Done
build-essential is already the newest version"[/COLOR]


I sudo lxc-start -n my32bitbox
then:
sudo apt-get build-dep wine 
cd $HOME 
mkdir wine32-tools 
cd wine32-tools 
~/wine-git/configure  [COLOR=#ff0000][ here it cannot find gcc - even if i put in the precise path to there - a lot of other comands is a no-go too - ]
[/COLOR]
*Please help *[/FONT]

---

