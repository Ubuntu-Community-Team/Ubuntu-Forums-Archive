---
title: "clout-init, autoinstall and local repository"
date: 2024-05-30
forum: Server Platforms
---

### Post by kelvorel on 2024-05-30
Hello,

I am working to build a custom Ubuntu ISO which can be installed on computer without internet. 
The purpose is to include in the file systems of the installed computer, a local repository located in (e.g) /opt/my_local_repo/

Previously, I was using a user-data file to setup the autoinstallation and to use a local user-data file (located in the ISO), I used the nocloud option in the grub. 

To use my local repo, I was doing something not very clean but it worked. 
I was extracting Ubuntu-Server LiveCD and adding directly the local repository in the .squashfs file. 
Then, using chroot, I was modifying the /etc/apt/sources.list to comment everything and adding my own sources in /etc/apt/source.list.d/
Finally, I was doing an "apt update" and then I was rebuilding the ISO and it worked perfectly. 

However, this process does not work on Ubuntu 24.04 for some reason I do not understand. 

So I was trying to figure out how to process differently using the cloud-init features. 
I continued to put my local repository manually in the .squashfs file in /opt/
But I tried to configure apt using "user-data" as follows:

[COLOR=#ffffff][FONT=Droid Sans Mono][COLOR=#569cd6]...
apt[/COLOR][COLOR=#ffffff]:[/COLOR]

[COLOR=#ffffff]    [/COLOR][COLOR=#569cd6]preserve_sources_list[/COLOR][COLOR=#ffffff]: [/COLOR][COLOR=#569cd6]false[/COLOR][COLOR=#ffffff]  [/COLOR]

[COLOR=#ffffff]    [/COLOR][COLOR=#569cd6]sources[/COLOR][COLOR=#ffffff]:[/COLOR]
[COLOR=#ffffff]      [/COLOR][COLOR=#569cd6]repo1[/COLOR][COLOR=#ffffff]:[/COLOR]

[COLOR=#ffffff]        [/COLOR][COLOR=#569cd6]source[/COLOR][COLOR=#ffffff]: [/COLOR][COLOR=#ce9178]"deb [trusted=yes] file:///opt/my_local_repo_folder/repo1 ./"[/COLOR]

[COLOR=#ffffff]        [/COLOR][COLOR=#569cd6]keyid[/COLOR][COLOR=#ffffff]: [/COLOR][COLOR=#ce9178]""[/COLOR]

[COLOR=#ffffff]      [/COLOR][COLOR=#569cd6]repo2[/COLOR][COLOR=#ffffff]:[/COLOR]

[COLOR=#ffffff]        [/COLOR][COLOR=#569cd6]source[/COLOR][COLOR=#ffffff]: [/COLOR][COLOR=#ce9178]"deb [trusted=yes] file:///opt[/COLOR][COLOR=#ce9178]/my_local_repo_folder/[/COLOR][COLOR=#ce9178]repo2 ./"[/COLOR]

[COLOR=#ffffff]        [/COLOR][COLOR=#569cd6]keyid[/COLOR][COLOR=#ffffff]: [/COLOR][COLOR=#ce9178]""[/COLOR]
[COLOR=#ffffff]  [/COLOR][COLOR=#569cd6]package_update[/COLOR][COLOR=#ffffff]: [/COLOR][COLOR=#569cd6]true[/COLOR]
[COLOR=#ffffff]  [/COLOR][COLOR=#569cd6]package_upgrade[/COLOR][COLOR=#ffffff]: [/COLOR][COLOR=#569cd6]false[/COLOR]

[COLOR=#ffffff]  [/COLOR][COLOR=#569cd6]packages[/COLOR][COLOR=#ffffff]:[/COLOR]
[COLOR=#ffffff]  - [/COLOR][COLOR=#ce9178]build-essential[/COLOR][COLOR=#ffffff] 
...
[/COLOR]

[/FONT][/COLOR]

I am testing the autoinstallation in a Virtual Machine. 
Doing this, the autoinstall fails. When I select the option in the grub to perform the autoinstall with my user-data configuration, it does the manual installation. 


If I remove the line: [COLOR=#569cd6]preserve_sources_list[/COLOR][COLOR=#ffffff]: [/COLOR][COLOR=#569cd6]false[/COLOR][COLOR=#ffffff]  [/COLOR]
It is detected and starts to perform the autoinstall but it failed at: 

"curtin command apt-config"

When checking the /etc/apt/source.list, repo were not updated.

---

