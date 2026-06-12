---
title: "Can't figure out text-mode installer command"
date: 2017-10-23
forum: Server Platforms
---

### Post by DarkMorford on 2017-10-23
I'm trying to set up an automated VM installer using [Packer]("https://www.packer.io"), and I'm having trouble getting the Ubuntu installer to start. I'm able to leave the pseudo-graphical install menu and drop out to a simple [FONT=courier new]boot:[/FONT] prompt, but I can't proceed from there. No matter what I enter, I get bounced back to the language-selection menu.

The command line I'm currently attempting to run is:
```
/install/vmlinuz vga=788 preseed/file=/floppy/preseed.cfg preseed/interactive=true initrd=/install/initrd.gz quiet ---
```

How do I get the actual installer process to kick off, and do I have the path to the floppy disk correct?

---

### Post by LHammonds on 2017-10-24
This is to create a template to crank out multiple Ubuntu Servers in a virtual environment?

Why not just install and configure Ubuntu Server and convert it to a template (in VMware).  Then deploy from template and you should only need to change the name and IP address.

Packer looks interesting but I don't see the point if you are in a VMware environment.  Would seem much more pertinent if installing bare-metal on many physical machines.

LHammonds

---

### Post by DarkMorford on 2017-10-24
I use different virtualization environments (VMware, VirtualBox,  Parallels) on different computers for a variety of reasons, and I want  to have an identical (or as close as I can get) VM on each of them.  Packer can generate all of these automatically instead of me having to  sit and configure Ubuntu on each one. Plus, there's something to be said  for having the machine configuration in source control so it can easily  be replicated on a new host if necessary.

---

### Post by DarkMorford on 2017-10-24
After further investigation, it seems that something is wrong with the bootloader on the 16.04.3 server install image. 

Using the following Packer script, a 14.04.5 image launches the installer as expected. If I change it to 16.04.3, however, no matter what I type at the [FONT=courier new]boot:[/FONT] prompt I am thrown back to the bootloader's language selection menu, and I'm unable to get into the installer itself.
```

{
    "builders": [
        {
            "type": "virtualbox-iso",
            "guest_os_type": "Ubuntu_64",
            "iso_url": "http://releases.ubuntu.com/14.04.5/ubuntu-14.04.5-server-amd64.iso",
            "iso_checksum_url": "http://releases.ubuntu.com/14.04.5/SHA1SUMS",
            "iso_checksum_type": "sha1",
            "ssh_username": "vagrant",
            "ssh_password": "vagrant",
            "disk_size": "32768",
            "boot_command": [
                "<enter><esc><enter>",
                "install file=/cdrom/preseed/ubuntu-server.seed ",
                "vga=788 initrd=/install/initrd.gz quiet ---",
                "<enter>"
            ]
        }
    ]
}

```

EDIT: I just tested with a 17.10 server ISO and the script worked as expected. Clearly there's something not quite right with the image for 16.04.3.

---

### Post by cariboo on 2017-10-25
I'd suggest submitting a bug about the problem, since you aren't sure what is causing the problem use:

[code]ubuntu-bug linux{/code]

---

