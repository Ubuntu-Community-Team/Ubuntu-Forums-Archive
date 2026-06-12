---
title: "Bad signature on system76 repository?"
date: 2012-04-27
forum: System76 Support
---

### Post by mgolden on 2012-04-27
When I do sudo apt-get update, I am seeing this:

W: GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures were invalid: BADSIG 176A5C84ED67C9ED System76 Development (System76 Development Package Signing Key) <dev@system76.com>

Do other people see it as well?  What does one do to get rid of it?

---

### Post by isantop on 2012-04-27
Download the latest version of the driver from [http://planet76.com/](http://planet76.com/). After you've got that, go ahead and install the package, then run the restore function. This will reset the repository information and ensure that this doesn't interfere with your updates.

---

### Post by mgolden on 2012-04-28
Seems to have done it for me - thanks.

---

### Post by h.thomas on 2012-05-15
Hi!

I am having the same problem as the OP reported, so I followed the instructions above (downloaded the newest version of the driver (2.7.4), installed it, and ran "restore system").  It did not fix the problem for me.  I am running oneiric on a lemu1. 

The final part of the output from sudo apt-get install is below:

W: GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures were invalid: BADSIG 176A5C84ED67C9ED System76 Development (System76 Development Package Signing Key) <dev@system76.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release) 

W: Some index files failed to download. They have been ignored, or old ones used instead.

***

Any sugestions on what I should do next?  Thanks!

Hugh

---

### Post by isantop on 2012-05-15
> **h.thomas said:**
> Hi!

I am having the same problem as the OP reported, so I followed the instructions above (downloaded the newest version of the driver (2.7.4), installed it, and ran "restore system").  It did not fix the problem for me.  I am running oneiric on a lemu1. 

The final part of the output from sudo apt-get install is below:

W: GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures were invalid: BADSIG 176A5C84ED67C9ED System76 Development (System76 Development Package Signing Key) <dev@system76.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release) 

W: Some index files failed to download. They have been ignored, or old ones used instead.

***

Any sugestions on what I should do next?  Thanks!

Hugh

Open up the Update Manager, then click on the Settings... button. Click on the Third-party software tab, then remove any entries there to System76. Then, run the driver's restore function again. Does that fix it?

---

### Post by h.thomas on 2012-05-15
Hi!

Thanks for your suggestion.  Running the Update Manager, I went to Settings, then in "other software" I unchecked planet76.com, and reran "restore system".  

I got a slightly different set of error messages (see below) -- one of the BADSIGs is not being complained about anymore.  But it still isn't working.  The output is below.  

In same "settings" window, under the "authentication" tab, it looks like there are signatures listed.  Should I try removing the ones that aren't working?  (Or, when you said I should remove mentions of System76, should I have removed the System 76 signature from here as well?)

Thanks for your help.  

cheers,

Hugh

**

W: GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures were invalid: BADSIG 176A5C84ED67C9ED System76 Development (System76 Development Package Signing Key) <dev@system76.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by isantop on 2012-05-16
> **h.thomas said:**
> Hi!

Thanks for your suggestion.  Running the Update Manager, I went to Settings, then in "other software" I unchecked planet76.com, and reran "restore system".  

I got a slightly different set of error messages (see below) -- one of the BADSIGs is not being complained about anymore.  But it still isn't working.  The output is below.  

In same "settings" window, under the "authentication" tab, it looks like there are signatures listed.  Should I try removing the ones that aren't working?  (Or, when you said I should remove mentions of System76, should I have removed the System 76 signature from here as well?)

Thanks for your help.  

cheers,

Hugh

**

W: GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures were invalid: BADSIG 176A5C84ED67C9ED System76 Development (System76 Development Package Signing Key) <dev@system76.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

Yes, you'll want to remove (not just uncheck) all of the system76 repositories and signatures.

---

### Post by h.thomas on 2012-05-16
I removed the signature, and that made the complaint about the System76 signature go away, but sudo apt-get update still had the same other complaints.   

I then found this thread:

[http://ubuntuforums.org/showthread.php?t=1753045](http://ubuntuforums.org/showthread.php?t=1753045)

and the course of action suggested there seems to have fixed the problem entirely.

(Though, even before I did this, the update manager did manage to find one file to install, so maybe things were working properly without the second step, though, as I said, I did still see some error messages.)

Thanks for your help!

---

