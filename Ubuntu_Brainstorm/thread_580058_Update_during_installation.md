---
title: "Update during installation"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by k99goran on 2007-10-18
I don't know if this is possible, but I have some ideas for the Ubuntu installer.

Would it be possible to have an installation process like the following?

0. The "Install" button has been double-clicked.
1. Offer a choice between a "clean" direct-from-CD installation, and an updated installation.

If updated installation is chosen:
2. Show one step of the installation process similar to what is available in Easy Ubuntu, that allows the user to easily select proprietary codecs and video drivers among other things (extras).
3. Have the installer check for software updates while step (1) is shown.
4. Download the updates and the extras to RAM while the user edits regional and partition setting.
5. Install the files that do not require updating directly from the CD (downloading continues if not finished).
6. If the updates and extras are downloaded, install them from RAM. If not, show a progress bar.
7. If working properly, you have just saved some time and possibly a couple of restarts.

---

### Post by bethaviv on 2007-10-18
Love this idea =)

It'll prevent some issues from the get go.

---

### Post by Twintop on 2007-10-18
I like this idea a lot too, but there might be some wrinkles to iron out if it does it implemented.

> 2. Show one step of the installation process similar to what is available in Easy Ubuntu, that allows the user to easily select proprietary codecs and video drivers among other things (extras). I'm not sure about the legalities involved with this. There is a reason they aren't included on the CD, but I don't know if the same conditions could prohibit this.

> 
4. Download the updates and the extras to RAM while the user edits regional and partition setting.
5. Install the files that do not require updating directly from the CD (downloading continues if not finished).
6. If the updates and extras are downloaded, install them from RAM. If not, show a progress bar. Three thoughts come to mind:[LIST]
[*]Why not use swap to store the downloaded files
[*]What happens if someone is installing on a system with a small hard drive and/or low memory? Disable this feature?
[*]If it is close to the next release and a large majority of the packages have been updated, how difficult would it be to download and install in 'chunks' so that it grabs files in a sane matter?[/LIST]Just some thoughts...

---

### Post by k99goran on 2007-10-19
> **Twintop said:**
> I'm not sure about the legalities involved with this. There is a reason they aren't included on the CD, but I don't know if the same conditions could prohibit this.
The user must still choose to install the codecs by checking a box, so I don't see how it is much different from making them available in synaptic.
> Why not use swap to store the downloaded files?
Personally I never use swap, but this is of course one solution.
> What happens if someone is installing on a system with a small hard drive and/or low memory? Disable this feature?
Or in that case the updates could be downloaded directly to the partition where Ubuntu is to be installed (starting after the partition has been chosen and formated). If both the hard drive and the RAM is so small that this feature will not work, then the users computer would probably not meet the system requirements and would not be able to run a regular update anyway. This method should in the end require less storage capacity as you don't need two versions of files.
> If it is close to the next release and a large majority of the packages have been updated, how difficult would it be to download and install in 'chunks' so that it grabs files in a sane matter?
Do you mean like a service pack?

Of course, there would be instances where this feature would not be available, like when the user doesn't have a working internet connection.

---

### Post by Zdravko on 2007-10-19
Nice idea.

---

