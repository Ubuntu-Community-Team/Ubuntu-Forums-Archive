---
title: "sudo apt-get install problem in Lubuntu 16.04"
date: 2016-04-28
forum: Virtualisation
---

### Post by West Swan on 2016-04-28
Hello,

I came up with the following sudo apt-get install command in a separate post with the help of people on this forum :-)

All these games are installed using the command on Lubuntu 14.04 but with Lubuntu 16.04 there are just errors.  The specific errors are "E: unable to locate package 0AD"  etc etc etc for all the games.  

I am testing this using VirtualBox if that has any bearing.

The command is: [FONT=&amp]sudo apt-get install 0AD 3dchess Airstrike AlienBlaster Amphetamine Armagetronad AsciiJump Asylum Atomix Balder2D Barrage Wesnoth Berusky Billard-GL Biniax2 BlackBox Blobandconquer Bloboats Blobby Blockout2 BrainParty BTanks Bygfoot Chromium-BSU DesMuMe Dosbox Einstein ExtremeTuxRacer Five-Or-More Flare FooBillard Four-In-A-Row Freedroid Frozen-Bubble FunnyBoat Gcompris Gnome-Hearts Gnome-Klotski Gnome-Mastermind Gnome-Mines Gnome-Nibbles Gnome-Tetravex Gnubik Gnugo GTKAtlantic Gunroar HoldingNuts Iagno LBreakout2 LightsOff LiquidWar LTris Maelstrom Mahjongg Megaglest Minetest Mokomaze Monsterz Moon-Lander Nestopia Netpanzer Neverputt Neverball OpenArena Performous Pingus PlayOnLinux Quadrapassel Radiotray Scorched3D SlimeVolley Smc Smc-Music Snake4 Snowballz STEAM Stella Sudoku SuperTux Super Swell-Foop TuxKart Tali Tennix Tetzle Teeworlds Tomatoes Transcend Warzone2100 Widelands XMoto Yabause Zaz ZSNES

Could someone help please?

Regards,

Paul
[/FONT]

---

### Post by vasa1 on 2016-04-28
1. Try using lower case
2. Mahjongg should be gnome-mahjongg
3. Sudoku should be gnome-sudoku

for starters ...

And are you sure you've enabled the universe repository?

---

### Post by West Swan on 2016-04-29
> **vasa1 said:**
> 1. Try using lower case
2. Mahjongg should be gnome-mahjongg
3. Sudoku should be gnome-sudoku

for starters ...

And are you sure you've enabled the universe repository?


You sir are a steely eyed missile man.

Brilliant.  The correct command using lower case is:

sudo apt-get install 0ad 3dchess airstrike alienblaster amphetamine armagetronad asciijump asylum atomix balder2d barrage wesnoth berusky billard-gl biniax2 blackbox blobandconquer bloboats blobby blockout2 brainparty btanks bygfoot chromium-bsu desmume dosbox einstein extremetuxracer five-or-more flare foobillard four-in-a-row freedroid frozen-bubble funnyboat gcompris gnome-hearts gnome-klotski gnome-mastermind gnome-mines gnome-nibbles gnome-tetravex gnubik gnugo gtkatlantic gunroar holdingnuts iagno lbreakout2 lightsoff liquidwar ltris maelstrom gnome-mahjongg megaglest minetest mokomaze monsterz moon-lander nestopia netpanzer neverputt neverball openarena performous pingus playonlinux quadrapassel radiotray scorched3d slimevolley snake4 snowballz steam stella gnome-sudoku supertux super swell-foop tali tennix tetzle teeworlds tomatoes transcend warzone2100 widelands xmoto yabause zaz zsnes


Thank you very very much!

---

### Post by Bucky Ball on 2016-04-29
*Thread moved to **Virtualisation**.*

---

### Post by West Swan on 2016-04-29
> **Bucky Ball said:**
> *Thread moved to **Virtualisation**.*

Hi Bucky Ball.

I can confirm that the solution by vasa1 works both in Virtualbox and also on a Pentium 4 that I just tried it on.

Regards,

Paul

---

### Post by vasa1 on 2016-04-29
West Swan, please take a look here: [http://ubuntuforums.org/showthread.php?t=2322576](http://ubuntuforums.org/showthread.php?t=2322576)

And you can mark this thread [SOLVED] if it is: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads). Though I request you to clarify whether the change of case was necessary or it was just a matter of enabling *universe*. Thanks!

---

