---
title: "Input/output error on HyperV Vagrant Linux virtual machine"
date: 2018-02-12
forum: Virtualisation
---

### Post by skinneejoe on 2018-02-12
[COLOR=#242729][FONT=Arial]I have a vagrant VM hosted in HyperV on my Windows 10 laptop. It is running Ubuntu 16. I've actually tried a few different Ubuntu 16 vagrant boxes to see if this was a problem with my particular box, but they all produce the same error when I try to list certain folders:
[/FONT][/COLOR]
**ls: reading directory '.': Input/output error**

[COLOR=#242729][FONT=Arial]The directory I'm trying to read holds my source code. It syncs using Vagrant SMB as a child directory of my project directory. The error was only happening in this directory, so I started systematically removing files and folders to see if one of them was causing an issue. After removing almost all the folders the 'ls' command would start properly listing the contents of the directory. So then I put some folders back and it broke again. What I came to realize is that it didn't seem to be any particular folder causing the issue, but instead the amount of data in the directory.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So I created a new test directory within my project and dropped a few images in it. I ran the ls command, it worked fine. Added a few more images, still worked. Added some more, and bingo it stopped working and gave the same error as above. Removed a few random images, and the ls command started working again.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So it seems to be related to the total file size in these directories. I have another vagrant VM I use on this machine for developing another project and I've never had this issue on it. But every VM I spin up, with different boxes now, seems to have this issue.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've read this can be a hardware problem, but I've run checkdisk on my laptop and there's no issues found. Furthermore this is a VM, so hardware should be abstracted away by the hypervisor layer.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It's a dynamic VHDX sized at 127Gb, and it's only expanded to ~5Gb.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any thoughts?[/FONT][/COLOR]

---

