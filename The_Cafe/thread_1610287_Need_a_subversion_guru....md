---
title: "Need a subversion guru..."
date: 2010-10-31
forum: The Cafe
---

### Post by hambone79 on 2010-10-31
I need some help from a subversion guru...

Just to give a little background, I have a Subversion server that I have been using for quite some time to manager 3D CAD data. This has been working very well for me, but recently I have been forced to switch from Linux to Windows for my CAD work and I'm having some issues...

To give everyone a better understanding of what I am trying to do, I have to explain how my CAD software (Pro/Engineer Wildfire 4.0) functions. Let's say I have a complete model of a lawn mower and I want to update a bracket for the muffler. The proper way to do this is to check out the model that I want to work on and place it in a working directory, then pull all of the other parts for the mower from a read only share that contains all of the files on my subversion server. By doing this I am only able to update the muffler bracket and I can't accidentally make changes or accidentally bump up the revision level of the other parts.

With my old Linux setup I was mapping the Subversion server to my workstation using davfs2. By doing this I was able to create a read only copy of the subversion repository that Pro/E could pull the extra parts from. With my new Windows setup, I'm having trouble getting a read only copy of the subversion repository on the network where Pro/Engineer can see it. Windows 7 does not play nice with Subversion/WebDAV so the only solution I have found is to map the subversion repository to the subversion server using davfs2 then share it over the network with Samba.

Does anyone know of a way to directly share the subversion repository over Samba so that it is read only?

---

### Post by MadCow108 on 2010-10-31
why would you want a read only working copy?
the whole point of a vcs is that you can go back whenever you make a mistake.
Or better just don't commit the accidental change (= svn st before each commit and revert all accidental changes with svn revert files)

If this is too much work write a pre commit hook which checks this.

---

### Post by hambone79 on 2010-10-31
> **MadCow108 said:**
> why would you want a read only working copy?
the whole point of a vcs is that you can go back whenever you make a mistake.
Or better just don't commit the accidental change (= svn st before each commit and revert all accidental changes with svn revert files)

If this is too much work write a pre commit hook which checks this.

Let me clarify...

I do not need a read only working copy. I check out the working copy of the files I want to update using RapidSVN and place them in my Pro/E working directory. The issue is that the CAD models I check out have dependencies on other CAD models in the repository so I need read only access to all of the other files in the repository so Pro/Engineer can build the complete model. 

I don't want to check out all of the files every time because I work on multiple projects that are up to several gigabytes in size and I don't want to waste time copying data back and forth. Pro/E has a means of opening a portion of a huge model such as this but it must be able to see all of the files in the model for verification. For example, if I am working on the muffler bracket of a riding mower, I can check out the muffler bracket into my working directory. Next, Pro/E will verify all the files in the riding mower from the read only copy of the repository by reading some information in the header of each file. From here I can tell Pro/E to open only the engine and leave the rest of the riding mower models suppressed. By using this method I can work on a 10GB model but only open a few MB at a time.

Basically what I am trying to do is to imitate the way in which Pro/PDM or Pro/Intralink operate in a production environment.

---

