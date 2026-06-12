---
title: "Creating  A New Virtual Machine"
date: 2008-05-20
forum: Virtualisation
---

### Post by RandyRandola on 2008-05-20
Hello all. 

I have square eyes trying to figure out all of the things I need to transition from MS to ubuntu. Two laptops for friends and my own home desktop. 

I have looked and could not find two answers to two questions.

Basic setup going through the wizard.
- Local Host
- Virtual Machine Configuration - Typical
- MS Windows
- XP Pro

Now the questions
1 - Network connection
What are the pros and cons for each selection?

2 - Disk Size
What would be the best size since it states the size can never be larger than what I set here.
Going to use this for 4 - 5 programs I need till I don't need them anymore. 
Can I delete this 'partition' once I don't need it anymore?

3 - What obvious (or not so obvious) questions am I missing? (Ok, there are 3 questions.)

Yes, I am new to ubuntu.

Thanks for all your help!

Randy

---

### Post by fjgaude on 2008-05-20
Go with NAT... later you can setup other connection types if you wish.

Answer all questions as the default... just hit Enter.

Use 10GB for the disk partition. That will give you all the needed space and allow you to use Snapshots. You'll understand that later as you use the VM.

Yes, you will be able to simple delete the huge file when you no longer need VM or vmware.

You are dealing with very advanced software and the manual takes days to fully understand. No need to fully understand but just about any question we have answer is found there.

Good luck but do let us know how you do.

---

### Post by RandyRandola on 2008-05-20
Thanks Frank.

XP installed.
VM Tools installed. 

Now. 

How to enable Virtual XP Pro to access the internet?
And how to manually enter additional hardware (i.e sound card)?

Thanks again for your help. I am also looking through the forums for the answer. Lots of reading and getting square eyes again...

Randy

---

### Post by fjgaude on 2008-05-20
Now, go to Edit/Preferences menu on the console. See the options you have, especially the Display, check both items if you wish automatic screen sizing.

Also, power off the VM, and then go to the VM tab menu and Settings. You can only set most of these when the VM is powered down. At the bottom find Add and from then on you can do as you will.

When I leave the VM I usually Suspend, then Exit the console. When I come back most of the things simply pop up, fast. The whole process is quicker than in a direct boot into Windows.

Let us know how you are doing, if you have any questions.

---

### Post by RandyRandola on 2008-05-20
I was wondering why all of the items were grayed out. Once VM powered down, piece of pie.

Sound works great.
Could only access the net when I changed from NAT to Bridged. I guess I don't know enough about NAT. 

Excellent idea about suspend instead of powering down, Much quicker!

Nothing more needed at this point. Everything is running really well. Will install those MS legacy apps and see what happens.

Thanks again Frank!

Randy

PS I see your Thank Yous on your profile - where can I thank you so it appears there?

---

### Post by fjgaude on 2008-05-20
Glad we were able to help... you thank folks by clicking on the yellow star icon that appears at the bottom, right of the post that helped.

Each day we learn as we are open to new knowledge, long live Ubuntu:

"A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed." -- Archbishop Desmond Tutu, 1999

---

### Post by kaginken on 2008-05-20
Here's a great reference for winblows guests, I disabled all these unnecessary services and it was much faster!

[http://ubuntuforums.org/showthread.php?t=646613](http://ubuntuforums.org/showthread.php?t=646613) 

Hope that helps!

Rock on :guitar:

---

