---
title: "My Ubuntu Small Business Server"
date: 2011-08-12
forum: Testimonials &amp; Experiences
---

### Post by mitanc on 2011-08-12
Hey All,

I just got thru a number of small things with my linux server and felt like posting about my experiences.  Think of it as a review of running linux servers.

A little backstory, I am an American who currently lives in China.  I set up a company here about 8 years ago.  We manufacture and produce accessories which are exported to the US.  I have an IT background, studied computer science in College and am a closet nerd in my spare time.  After my office grew I decided I needed a server to handle the number of users and work we were doing.  Because stuff is so cheaper here I went to the computer market and purchased a custom server with intel based motherboard.  The guys there offered to install Microsoft Small Business Server on it (for free, i.e. pirated) and I went on from there.

For a while this solution worked, but eventually ran into license issues with too many users logging in.  After deciding not all of my users needed to be on the domain I temp solved that issue.  I used the built in backup solution and let it do its thing nightly.  After a while the server got slow, people had trouble pulling up files that were being served.  Print jobs would get stuck.  Then the unthinkable, the server wouldn't boot.

After all this I called the tech guys to see if they knew of a quick way to fix it.  Their solution was to reinstall windows and start again.  I said alright I got a  backup lets go.  Now all my data was on separate hard drives than the OS so data wasn't my problem, I was just dreading reconfiguring the damn thing.  After reinstalling, the backup would not restore, some weird error and I couldn't be bothered to reconfigure this thing.

Now, all this time I have been tinkering with linux on my home desktop.  I started playing with Red hat and slack ware back in the day then debian and then finally ubuntu.  I felt I had the knowledge needed to make a server which the office would use everyday.  

I went back the computer store and got a new server with more ram bigger space etc and decided this is what was going to be done.  Went online read some HOW TOs and setup software raid on Ubuntu 8.04LTS.  After that was done I figured out samba and setup the server as a PDC with roaming profiles.   

After reading everything and getting started it took me about 2 days to get it up and running.  I moved the data, setup permissions and added the XP clients to the machine.  Eventually the whole office was using this thing and it was doing a great job.  

Wow, I was impressed, this does everything a full fledged windows server does for FREE!  More than free, since I live here in China and 90% is pirated, it was just headache free.  I had uptime of over 100 days and reboots only because of power outages in the area.  The thing kept chugging.  

Eventually as my business grew I had clients request FTP sites with photos of items we were shipping.  I said hmm, I can do that and now setup nightly sync between my server and clients FTP sites.  All this enabled me to make more money by selling more stuff by adding these services to my clients.  

Then I worried about backups.. I got rsnapshot for nightly backups and I use an online backup solution and setup rsync for that.  Okay, so I got RAID, nightly backups on the server for the users, and weekly backups on the cloud.  I am pretty safe now.

Next step, I added a windows 7 client (my new desktop, I am the boss after all) and couldn't log in to the server.  This sucked, but had to upgrade my samba.  Got the info online and it required compiling from source and updating samba.  I was worried it could hose my current setup so using tar I backup up the system files (basically / minus home directories and data which were on different partitions)  After I backed up and threw the tar on a different partition I began updating the system.  I actually screwed something up and samba ldap and all that stopped working.  I untard the backup back into / and everything was back to normal.  This was amazing.

I redid it, got it working and did a system backup again.  Now if anything gets hosed can resume from the old backup.  

All in all, this OS is enabling me to run like a much larger company with IT staff.  I have clients who work with huge factories in China, but I offer them better service and cheaper prices because of the tech ability I have.  

The thing with linux is its a community, everyone is building small parts that eventually work together.  Not everything plays nicely, so it involves a little tweaking on the setup side.  But once its setup this thing is a rock.  It does everything you want and more.  In the day of GUIs, mice, AJAX, web, etc. all I need is a little box which I can SSH into to do it all.  

In the long run I have probably saved thousands of dollars and made more because of this little server.  I imagine that this thing can run for another 10 years if the hardware holds up.  I am shocked and amazed that a community can do this.

Thank you Linux, thank you Ubuntu, and thank you to the community.  Oh yeah, a BIG thanks to Google and that search button on ubuntuforums.org.  

In the meantime I was so impressed I installed a media server in my home.  This thing downloads all the US tv shows I miss because I live in China off of newsgroups.  XBMC on my appletv reads the drive and has the ability to play all these files.  Plex installed on the linux server allows me to convert on the fly files that can't natively play on the Apple TV. Airvideo server on linux allows me to view on my iPad and iPhone.  My work server backs up relevant data I need to this box so I can work from home (telecommuting baby!) and whatever else I can figure out to do I'll do it.

I love these machines and I am so proud of being the administrator!  

Tell me about your stories and if you have any comments would love to hear them.  Thanks to all again!

---

### Post by Porcini M. on 2011-08-12
Glad it worked out for you! :cool:

---

### Post by Perfect Storm on 2011-08-13
Moved to Ubuntu Testimonials & Experiences.

---

### Post by papibe on 2011-08-13
That is an amazing story. Thanks for sharing it!!

Personally I think Ubuntu as a Linux distribution is great. However, I believe that the biggest Canonical's achievement is to create and maintain one of the best (if not the best) communities around.

Kind Regards.

---

### Post by zero244 on 2011-08-15
That was a very interesting real life testimonial.
I think it amazes most of us that such high quality software is available for free.

It is surprising that China more or less sanctions pirating not only software, but music and movies and anything else they can make a buck on.

---

### Post by mitanc on 2012-03-22
Thanks for the feedback.

Yeah, I am a nerd by trade, but work overseas in the fashion and manufacturing sector now.  I am just so happy that I still have my own ways to work with technology and its helping me be more successful.

Would love to hear anyone else who's done cool stuff.

---

### Post by mastablasta on 2012-03-22
we are running our website, webstore and well basically all (but the online banking) on Linux.If only they made the banking compatible...
and also i use a linux host (for web stuff), as it is cheper for us than to have a server at home. high uptime, really stable, had 0 issues so far.
Web design and all is done at home on linux mashcine as is all correspondence with clients etc.

additioanlyl you might be interested in Ubuntu based distributions that specialise in making easy to use servers (the OS i mean) for smlal businesses. for example Zentyal. i think they might need less tweaking on install.

---

