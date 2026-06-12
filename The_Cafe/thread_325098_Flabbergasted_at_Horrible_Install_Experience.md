---
title: "Flabbergasted at Horrible Install Experience"
date: 2006-12-25
forum: The Cafe
---

### Post by batbelt on 2006-12-25
I am astounded at the confluence of errors that I experienced when attempting to install Kubuntu. A colleague recommended that I try KDE and recommended this distribution.

I would like to solicit comments on my experience so that I can better understand how the situation I encountered came to be.

The following is a copy of the message I sent to my colleague:


Greetings!

This is [me] from [computer service organization]

Here is how I've spent my time just lately:

Had a PC with W2K Pro on it. Set up partitions in
anticipation of loading Kubuntu.

Loaded Kubuntu 6.10 Edgy. The installation just stared
at me. Turns out qtparted was sucking up all the CPU.

No problem. That's what I get for dealing with
bleeding-edge ware.

Fall back to Kubuntu 6.06.1 Dapper. Same thing.

Research. Turns out to be a known problem. Delete all
the Linux partitions I created. I will create them
during the Kubuntu install instead.

Load Kubuntu 6.06.1 Dapper. Choose manual
partitioning. Create the partitions.

I noticed that even though I had typed in partition
labels, they are not being displayed. If I select the
partition and do a format, I get another opportunity
to supply a label.

Okay, so I format my first Linux partition and give it
a label. Whoa! Look what I did. I must have selected
the very next partition by accident. It did not format
/dev/hda6, I formatted /dev/hda7 (seven) by accident.
I am so stupid. I am worthless. I wiped out my W2k
transient partition. No big loss. Let's go fix it.

I selected the clobbered W2K transient partition
(/dev/hda7), chose NTFS, and supplied a label. It
formats it.

No it didn't.

The mother-luvin fscking bastige WENT AND FORMATTED
/DEV/HDA8!!! Turns out I didn't screw up, the
partitioner did. qtparted in the blessed official
"please-use-this-one" version doesn't format the
partition you told it to do, IT FORMATS THE ONE THAT
COMES RIGHT AFTER THE ONE YOU PICKED OUT!

This can't be right. It must have the table wrong. I
hit the "Go Back" button and then choose manual
partitioning again. I figure that it just needs to
read the table in again from scratch and everything
will look alright again.

Maybe that is what would have happened. I'll never
know. The qtparted bug description says that it has
trouble with Linux partitions made by other tools.
That is incorrect. It cannot handle THE LINUX
PARTITIONS THAT IT HAS MADE ITSELF! The partitioner
just stares at me again.

Let us pause here and have a moment of silence to
remember the W2K "Documents" that I have just
obliterated.

...

Ok, moment's over.

Howzabout we go fix things so I can at least get W2K
up again.

Fire up Partition Magic. Funny, even though I told
qtparted to make these partitions ext3 type, they are
showing up as "Linux ext2". Weird, huh? Oh well, who
cares. Let's just delete them HEY! PARTITION MAGIC
SAYS IT DOES NOT UNDERSTAND THE FILESYSTEM TYPE! IT
REFUSES TO DELETE THEM.

i    a m    i n    a    w o r l d    o f    s h y t t
e

I do not want you to tell me how to fix this. I have
already figured out how I can accomplish getting
Kubuntu installed if I choose to. I do not want you to
quiz me on my need to organize partitions in a certain
way. I realize that this shoddy craftsmanship is not
directly related to KDE. I do not want you to point
out where in the release notes this was covered. I do
not want you to supply impeccable justifications as to
why this fault was propogated from 6.06 to 6.10. I do
not wish to be directed to any newsgroups, web pages,
wikis, blogs where a warning and workaround are. I do
not want to know when this situation will be resolved.
I do not want help in recovering the W2K documents.

I always stayed away from KDE. I never had any trouble
with Ubuntu before. What I DO want you to do is
appreciate the reasons for my being negatively
interested in attempting to make use of KDE again.
That is, I don't think any amount of proselytizing
will get me near converting over to the dark side. So
be kind when you tell me all the neat things yours
does.

I thought I was getting a shiny red bike for
Christmas. Instead I got a burning sack of coals.
Ouch.

Peace!

---

### Post by po0f on 2006-12-25
batbelt,

I really don't see a point to this thread: are you asking for support or just wanting to "solicit comments"?  If it's the latter, there's a [better subforum](http://www.ubuntuforums.org/forumdisplay.php?f=11) for it.

If it's the former, I would suggest using the [GParted](http://gparted.sourceforge.net/) live CD to partition your hard drive before installation.  I've never used QtParted so I can't comment on your experience with it.

A quick search on the forums indicated that other users were having trouble with QtParted as shipped with Kubuntu.  Maybe a little research and a backup could have saved you this headache?  I'm surprised someone working at "[computer service organization]" doesn't have a backup for his data.  ;)

HTH.

---

### Post by Delta_Farce on 2006-12-25
Why are you blaming KDE for problems with the Installer? I've put several version of Kubuntu on my pc and it lives quite happily with XP and Vista, and I haven't had any of the partitioning issues that you've described (using the alternate install cd).

---

### Post by bulldog on 2006-12-25
We'll probably never know what issues this strange behavior of Qparted.
I'm sorry you had this bad experience.

I can only advice to use the next time the Gparted live cd,which has never caused me any trouble,which of course isn't a guarantee you won't have.

Did a fair amount of Ubuntu installations and never had this kind of trouble,but I have to admit,the partitioner isn't very clear about the things it does.:(

---

### Post by swlbc on 2006-12-26
I know exactly how this person feels .. working dilengently on a project an' following all the "helpful" information garnered from experienced user's ... for what ? an error message of some sorts that tells you that it's overwritten everything it could find an' it is sorry if this is an inconvenience to you > an' have a good day !! plzzzz ...

Of what I've seen on these forums with regards to what others are using for PC's we don't all have mazerratti's for computers with endless amounts of expensive RAM nor time to spend fixing all the problems these distro's create .. it seems you fix one problem an' that in turn breaks somthing else an' your back again chasing the proverbial dragon.

If you only want to do ONE thing at a time, and don't expect too much at that ~ then these O/S are for you.

---

### Post by Sef on 2006-12-27
> I do not want you to tell me how to fix this.

Ok.  Moving this thread to Ubuntu forum then.

---

### Post by Sef on 2006-12-27
> Fire up Partition Magic. Funny, even though I told
qtparted to make these partitions ext3 type, they are
showing up as "Linux ext2". Weird, huh? Oh well, who
cares. Let's just delete them HEY! PARTITION MAGIC
SAYS IT DOES NOT UNDERSTAND THE FILESYSTEM TYPE! IT
REFUSES TO DELETE THEM.

Some advice for people other people reading this thread:

Don't use Partition Magic.  It and LInux tend not to get along.  As Bulldog says, get [GParted]("http://gparted.sourceforge.net").  It works great and is no cost.

---

### Post by mistamcgoo on 2006-12-27
Both for Kubuntu and ubuntu, i just make some free HD space in windoze 2k or xp, 
10 gb or so, boot up the install cd, and let it automatically partition the free space for me during the installation process
I never do any manual partition making before the installation process, 
Has worked flawlessy each and every time so far.

---

### Post by smoker on 2006-12-27
a backup is an essential necessity before any repartition work. that's commonsense, doesn't matter what partition app you use!

---

### Post by msjulie on 2006-12-27
Dear Batbelt,

Sorry, about your lost files.

Everybody makes assumptions in life and in the computer world; otherwise, nothing would ever get done.

In this case you assumed the partitioner would behave appropriately.  I'm sorry that it didn't.

It is disturbing that as you said that an issue like this would make it from one distro to the next.  I've heard of other hickups with the installers partitioner.

Unfortunately, this world nor this OS is ideal--flawless.  So you always must make backup of your work (as others have noted.)  I learned this lesson in my childhood:  After many hours of programming, quickly type a wrong command or have a computer glitch arise and destroy my work.  Ouch!  Gone forever. A painful lesson learned.

Yes, those files of yours will be missed--good-bye.

You decided not to trust KDE.  That is an over reaction.  A little prudence goes a long way.

Julie

---

