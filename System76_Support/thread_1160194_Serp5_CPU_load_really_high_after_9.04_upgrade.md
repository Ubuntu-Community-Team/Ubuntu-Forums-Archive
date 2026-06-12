---
title: "Serp5 CPU load really high after 9.04 upgrade"
date: 2009-05-15
forum: System76 Support
---

### Post by serval1 on 2009-05-15
I have held back from upgrading to 9.04 (64 bit) until after a business trip, well I did it today. It worked fine, however now I have an interesting CPU load. with 8.10, all four CPU's used to be at 2 to 10% when idle (indexing can chew some up). Now all 4 CPU's are running between 60 and 95%, even with indexing turned off.

Has anyone experienced a similar jump in CPU load? Is there a solution to get it back down? I looked at all the threads since 9.04 was released, and I did not see anyone else with this issue. I am on a Serp5.

Update - Right after I submitted this, the indexer service reported a corrupted index file. The tracker settings have changed in the update, and indexing took foreground priority. Without the tracker running, CPU is at normal levels.

---

### Post by thomasaaron on 2009-05-15
You have a very bad tracker bug that is going to utterly chew up your filesystem.

Do this...

sudo apt-get install tracker-utils
tracker-processes -r 

...now.

---

### Post by serval1 on 2009-05-15
Thanks, done....Is ths a common problem, or due to my configuration? Can I setup Tracker again?

---

