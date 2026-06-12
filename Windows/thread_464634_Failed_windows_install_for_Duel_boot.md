---
title: "Failed windows install for Duel boot"
date: 2007-06-04
forum: Windows
---

### Post by Sabar on 2007-06-04
Guys I don't know if I should be posting this here or not. I appoligize for the fact that this is not really an Ubuntu issue but I am really hoping someone can help me with his problem.

A few weeks ago I downloaded the new fiesty fawn, I decided to make life easier on my self and clean up the bloated windows I have ( XP ) by doing a full formatt and use the resource CD that came with my Alien ware to also make my empty space for the Linux Installation.

I have two Hard drives in my computer, Hard drive #1 is a 150 gig, and Hard Drive #2 is a 260 Gig drive.
HDD #1 I have been using for my O/S ( up untill recently Just windows ) and HDD #2 is a storage device for my pics and music

After downloading and burning Fiesty off I set about the task of reformatting my computer using the Resource CD ( XP Home ) privided with the computer by Alien. I Partitioned my HDD #1 so there was 110 Gigs of NTFS leaving 40 gigs unused for ubuntu.

I then installed Windows XP onto the 110 gig partition. and after I was done with that I ( with out checcking into any great detail that windows was alright, seemed to be at first glance ) Installed Fiesty onto the 40 gigs.

Now being excited to be a New linux user the first thing I notice and like is that both my drives are located on the background for easy access. and checking this out the first thing I did was going and see what all I could use that was already saved by Windows based programs ( Musicmatch for the music and HP for the Pics. ) To my delight things worked.

Now we go a few days further into my story and I have pics on my camera I was going to move to the computer so I go back to windows and start installing all the other programs when I notice I have no "D" drive. ( HDD #2 )

Right now If I go to

Quote:
Start > My Computer > Hard disk drives
Only one drive is listed, and If I right click on this one drive ( C ) then go to properties I am greated with a drive that is 114 Gigs ( out of origanally 150-160, somthing like that )

while under properties if I go to the drives tab I have for drives listed. one is a CD drive one is a Burner drive then what appears to be both my Hard drives

Quote:
HDS722516VLSA80 Disk Drives
HDS722525VLSA80 Disk Drives
Listed in that order I had some one at anouther web site tell me to

Quote:
Start > Run >, type; diskmgmt.msc
This gave me a report that both of my disks were Healthy and Active, HOWEVER! HDD #1 is desinated as "C" drive and HDD #2 is not named at all.

The same person also had me

Quote:
Start your system in recovery console mode, and from that prompt try a: CHKSDK D: /p /r
I hope I understood what I was told to do, being a resource CD I dont believe I have a Recovery Console so what I did was take a Cd of XP that some one burned off for me to fix anouther problem I had a while back, started the computer on that disk and it has a recovery option. I went thrue the proccess of getting the compter to run on that then when propted I typed in CHKSDK D: /p /r. The report that was generated at that point was

Quote:
The Volume appears to contain one or more Unrecoverable problems
ok Guys thats what i have done so far and this is all that I know.

I have everything on HDD #2 saved and burned off ( thank god ) so if I have to formatt it in some way to get windows to see it again what ever ( would rather not go that route, but it will work also )

Once again I appoligize if I should not have posted this here. I am a bit frustrated now and I am really looking for answeres. so if someone has any idea what is going on and how to fix it, please let me know. If you think there is some where else I should have posted this, thats ok too. Just please give me a link to the place.

Thanks everybody, for you patiance and understanding. with out you guys I would be in a world of Hurt. and stuck in the Windows cage.

---

### Post by Pragmatist on 2007-06-05
What exactly is your question?

---

### Post by pyros on 2007-06-05
If I am correct, you have two drives, one for your operating systems (#1), one for media (#2).
You can access the media drive (#2) in ubuntu, but not in windows.

Did you reformat or repartition your media drive when you were preparing the computer to install ubuntu and windows?

If you boot into ubuntu now, can you still access the media drive?

What file system type is the media drive formated in (fat32, ntfs, efs3, etc)?

---

### Post by smoker on 2007-06-05
> Quote:
Start > Run >, type; diskmgmt.msc
This gave me a report that both of my disks were Healthy and Active, HOWEVER! HDD #1 is desinated as "C" drive and HDD #2 is not named at all.

hi, if HDD #2 is showing in disk management, try 'right clicking' over it, and see if the option, 'change drive letter and paths...' is available. if so, nominate the drive as 'D' and restart and see if it now shows in my computer as drive 'D'. (please note though, if windows has used the 'D' tag for something else, eg, cd drive, or whatever, you will not be allowed to use 'D' twice, you'll have to rename whatever is using 'D' to someother letter first).

---

### Post by Sabar on 2007-06-05
Thank you for the responces guys.

pyros

Yes Drive #1 is for OS.  Drive two is media

Nope I did not reformat Drive #2. Infact I did not touch it at all during the instalation prosess of either Ubuntu or windows.

Drive #2 is still in its origanal NTFS formatt.

I can access Drive #2 from Ubuntu But not From windows 

Both Drives are Factory installed. Never had a problem when I blacnked out Drive #1 and reinstalled Windows Before ( about 3 times. You know a little bit of knowledge can really screw things up ;))


smoker 

I tried to right click on Drive #2 in disk managment however  'change drive letter and paths...' Is not an option. the only option I have there is to delete partition. dont know why this is.

Sorry for the spelling, but spell checking is not working right now for me either :(. One thing I can say is Ubuntu seems to be alot easier to install then windows ever is. )

Thanks for any info you guys can give me. Hell I would even be happy for links to windows web sites that people could help me on. God knows the one's from Microsoft are a pain in the *** to use and for there help its EXPENSIVE!!

What would happen if I reinstalled windows again? what would it do to my Ubuntu Install? I finnally have Ubuntu the way I like that now and dont want to mess that up.

Thanks again guys

Sabar

---

### Post by pyros on 2007-06-06
hmm, well. crap.
the first thing that I would do would be to install ntfsprogs, if they aren't installed already and run ntfsck in ubuntu.

---

### Post by pyros on 2007-06-07
If all else fails, you could reformat the drive from inside windows.

---

### Post by Sabar on 2007-06-07
What do I do to reformat the drive from windows? just go threw disk manager? I think that was one of the options. I have everything on that drive backed up so all I have to do is reinstall everything.thats no big problem.

---

### Post by pyros on 2007-06-08
yeah that's what I'd do. reformat from disk manager. just wish I knew why it is acting so strangly.

---

### Post by Sabar on 2007-06-10
Had some one lead me to test disk I am trying that right now and if that doesnt help then its formatting time

Thanks for all the help guys I really do apprieciat it

Sabar

---

