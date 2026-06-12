---
title: "creating Ubuntu VMs using packer"
date: 2014-03-11
forum: Virtualisation
---

### Post by launchpad-nomoreheroes on 2014-03-11
Has anyone here managed to use packer (See [www.packer.io](www.packer.io)) to create Ubuntu Desktop VM packages,which can be used with virtualbox, amazon etc ?

I've managed to use packer with Cent OS and Ubuntu Server editions, but for some reason no matter what I do I simply cannot connot configure packer to automatically build me a vanilla Ubuntu Desktop VM, for me to use with vagrant to create a variety of custom Ubuntu Desktop VMs for various different purposes.

Oh well, looks like no-one could help and I had to get there on my own.

For anyone else having the same problem, here is my packer json configuration to automatically build a Ubuntu Desktop VM and use it with virtualbox

The part I was struggling with was the boot command section.

```
{
  "builders": [{
    "type": "virtualbox-iso",
    "virtualbox_version_file": ".vbox_version",
    "headless": false,
    "vm_name": "Ubuntu13.10-Desktopx64",
    
    "guest_os_type": "Ubuntu_64",
    "disk_size": 40960,

    "iso_url": "../iso/ubuntu-13.10-desktop-amd64.iso",
    "iso_checksum": "21ec41563ff34da27d4a0b56f2680c4f",
    "iso_checksum_type": "md5",

    "boot_command": [
      "<esc><esc><esc><enter><wait>",
      "/casper/vmlinuz.efi url=http://{{ .HTTPIP }}:{{ .HTTPPort }}/ubuntu-13.10-Desktop-amd64/preseed.cfg automatic-ubiquity boot=casper initrd=/casper/initrd.lz quiet splash -- <enter>"
    ],
    "boot_wait": "6s",

    "http_directory": "../http",
    "guest_additions_path": "VBoxGuestAdditions_{{.Version}}.iso",
    "guest_additions_url":    "../iso/VBoxGuestAdditions_4.3.8.iso",

    
    "ssh_username": "vagrant",
    "ssh_password": "vagrant",
    "ssh_port": 22,
    "ssh_wait_timeout": "10000s",

    "vboxmanage": [
      ["modifyvm", "{{.Name}}", "--memory", "512"],
      ["modifyvm", "{{.Name}}", "--cpus", "1"]
    ],

    "shutdown_command": "echo 'vagrant'|sudo -S /sbin/halt -h -p"
  }],
  "post-processors": [{
    "output": "../build/ubuntu-13.10-Desktop-amd64.box",
    "type": "vagrant"
    
  }],
  "provisioners": [{
    "type": "shell",
    "execute_command": "echo 'vagrant' | {{.Vars}} sudo -S -E bash '{{.Path}}'",
    "scripts": [
      "../scripts/vagrant.sh",
      "../scripts/vboxguest.sh",
      "../scripts/compact.sh"
    ]
  }]
}
```

I am still having one issue, though, which is that at the end of the install there is a prompt to click before it will reboot.

If anyone can help that would be awesome! My preseed config has this line, which I thought would do the trick, but it doesn't:

"d-i finish-install/reboot_in_progress note"

Finally, some extra info to help with automated Ubuntu Desktop installs ... some extra questions that you can set answers for in your preseed, which relate specificly to the Ubuntu installer.

[https://wiki.ubuntu.com/UbiquityAutomation](https://wiki.ubuntu.com/UbiquityAutomation)

One of them is what you need to make Ubuntu installer perform a reboot automatically. The Debian d-i command for this does nothing.

God knows why there's no mention of this is in the official Ubuntu documentation for automatic installs! Instead its buried away in their documentation for Ubiquity, with no reference to it in their installation guide.

---

### Post by darrenleeweber on 2015-03-01
Thanks for posting!  I'm wanting to use packer with vagrant to specify and provision my preferred development environment using ubuntu desktop.  I'd be very interested to see related efforts, esp. anything that uses puppet to provision the development environment.  I'm wanting to specify a user account (other than vagrant) and setup a ruby (rbenv) installation, along with IDE tools like sublime text 3 and associated packages.

RE your .json file, what is the directory structure implied and the associated files?  Are they downloads or something for packer or did you manually create them?  When running packer validate on that json, it fails to find the scripts, i.e.

```

$ packer validate templates/ubuntu_desktop.json 
Template validation failed. Errors are shown below.

Errors validating build 'virtualbox-iso'. 3 error(s) occurred:

* Bad script '../scripts/vagrant.sh': stat ../scripts/vagrant.sh: no such file or directory
* Bad script '../scripts/vboxguest.sh': stat ../scripts/vboxguest.sh: no such file or directory
* Bad script '../scripts/compact.sh': stat ../scripts/compact.sh: no such file or directory

```


This github project looks relevant, see [https://github.com/rokhmanov/packer-teiid](https://github.com/rokhmanov/packer-teiid)

---

### Post by Douglas_Mendes on 2015-03-16
[FONT=Arial]Good afternoon everyone![/FONT]
[FONT=Arial]Dear Friend,[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I'm having trouble installing and configuring the packer and docker. Trying to build within the ubuntu 4.14 it shows the error below:
[/FONT]
[FONT=Arial]Build 'docker' errored: Retryable error: Error uploading script: Upload failed with non-zero exit status: 1
[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]settings into bash[/FONT]
[FONT=Arial][COLOR=#3d85c6](cloudvic-images)douglasm@douglas-B3:~/CloudVicProjects/cloudvic-images$ ./manage.py build templates/gedvic/gedvic-package-build/gedvic-package-build.json[/COLOR]
[COLOR=#3d85c6]Running: packer build -var tag=0.2 -var pwd=/home/douglasm/CloudVicProjects/cloudvic-images/templates/gedvic/gedvic-package-build templates/gedvic/gedvic-package-build/gedvic-package-build.json[/COLOR]
[COLOR=#3d85c6]docker output will be in this color.[/COLOR]
[COLOR=#3d85c6]
[/COLOR]
[COLOR=#3d85c6]==> docker: Creating a temporary directory for sharing data...[/COLOR]
[COLOR=#3d85c6]==> docker: Starting docker container...[/COLOR]
[COLOR=#3d85c6]    docker: Run command: docker run -v /tmp/packer-docker977648362:/packer-files -d -i -t ubuntu /bin/bash[/COLOR]
[COLOR=#3d85c6]    docker: Container ID: 75441e4449f1a1a90f03ad61f44fa970e8f99821af801419f92c8a67cbfdd941[/COLOR]
[COLOR=#3d85c6]==> docker: Provisioning with shell script: /tmp/packer-shell311100786[/COLOR]
[COLOR=#3d85c6]==> docker: Killing the container: 75441e4449f1a1a90f03ad61f44fa970e8f99821af801419f92c8a67cbfdd941[/COLOR]
[COLOR=#3d85c6]Build 'docker' errored: Retryable error: Error uploading script: Upload failed with non-zero exit status: 1[/COLOR]
[COLOR=#3d85c6]
[/COLOR]
[COLOR=#3d85c6]==> Some builds didn't complete successfully and had errors:[/COLOR]
[COLOR=#3d85c6]--> docker: Retryable error: Error uploading script: Upload failed with non-zero exit status: 1[/COLOR]
[COLOR=#3d85c6]
[/COLOR]
[COLOR=#3d85c6]==> Builds finished but no artifacts were created.[/COLOR]




These are the gedvic-package-build.json settings.

[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial][COLOR=#CC7832]{
[/COLOR][COLOR=#CC7832]  [/COLOR][COLOR=#9876AA]"variables"[/COLOR][COLOR=#CC7832]: {
[/COLOR][COLOR=#CC7832]    [/COLOR][COLOR=#9876AA]"pwd"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]""[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]    [/COLOR][COLOR=#9876AA]"tag"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]""
[/COLOR][COLOR=#6A8759]  [/COLOR][COLOR=#CC7832]},
[/COLOR][COLOR=#CC7832]
[/COLOR][COLOR=#CC7832]  [/COLOR][COLOR=#9876AA]"builders"[/COLOR][COLOR=#CC7832]: [/COLOR][
    [COLOR=#CC7832]{
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"type"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"docker"[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"image"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"ubuntu"[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"export_path"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"gedvic-package-build.tar"[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"pull"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#CC7832][B]false
[/B][/COLOR][COLOR=#CC7832]**    **[/COLOR][COLOR=#CC7832]}
[/COLOR][COLOR=#CC7832]  [/COLOR]][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]
[/COLOR][COLOR=#CC7832]  [/COLOR][COLOR=#9876AA]"provisioners"[/COLOR][COLOR=#CC7832]: [/COLOR][
    [COLOR=#CC7832]{
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"type"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"shell"[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"inline"[/COLOR][COLOR=#CC7832]: [/COLOR][[COLOR=#6A8759]"apt-get update --fix-missing && apt-get install aufs-tools && apt-get clean"[/COLOR]]
    [COLOR=#CC7832]},
[/COLOR][COLOR=#CC7832]    {
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"type"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"file"[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"source"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"{{user `pwd`}}/build.sh"[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"destination"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"/build.sh"
[/COLOR][COLOR=#6A8759]    [/COLOR][COLOR=#CC7832]},
[/COLOR][COLOR=#CC7832]    {
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"type"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"shell"[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"inline"[/COLOR][COLOR=#CC7832]: [/COLOR][[COLOR=#6A8759]"chmod +x /build.sh"[/COLOR]]
    [COLOR=#CC7832]}
[/COLOR][COLOR=#CC7832]  [/COLOR]][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]
[/COLOR][COLOR=#CC7832]  [/COLOR][COLOR=#9876AA]"post-processors"[/COLOR][COLOR=#CC7832]: [/COLOR][
    [COLOR=#CC7832]{
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"type"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"docker-import"[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"repository"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"cloudvic/images"[/COLOR][COLOR=#CC7832],
[/COLOR][COLOR=#CC7832]      [/COLOR][COLOR=#9876AA]"tag"[/COLOR][COLOR=#CC7832]: [/COLOR][COLOR=#6A8759]"gedvic-package-build-{{user `tag`}}"
[/COLOR][COLOR=#6A8759]    [/COLOR][COLOR=#CC7832]}
[/COLOR][COLOR=#CC7832]  [/COLOR]]
[COLOR=#CC7832]}[/COLOR][/FONT]

---

### Post by TheFu on 2015-03-19
Never heard of packer before and I don't use vagrant.

**My method:**
I have have a golden image for a minimal server, then add/remove packages using Ansible in a devops way to build servers or desktops.  So I clone the base VM in a few sec and build what I need based on purpose in the next 5-20 min. Also, using the same ansible playbooks to maintain these systems is trivial, should someone make unapproved changes underneath.

Looks like Packer and Ansible can be used together - [http://blog.codeship.com/packer-ansible/](http://blog.codeship.com/packer-ansible/) - this will be much, much, much less effort than using with puppet or chep or salt or ... any other devops tool. 

Clearly, if you are an ansible shop then this method makes sense.  Ansible uses yaml to control things, easy for humans, yet very powerful.  There is a 20 min video on "Ansible Quickstart" which explains much better than I can.  In 30 min, you can be managing all your machines on some level and in an hour, you'll be maintaining packages and settings for any number of similar machines.

I'll take a look at Packer - very interesting.

---

### Post by dragon-788 on 2015-03-23
Your trouble is that you need to use the ubiquity options not d-i options. See the page you linked on UbiquityAutomation. 


[LIST]
[*]**ubiquity/reboot**: automatically reboot when the installer completes. Be sure to add 'noprompt' to the kernel command line to also skip the "please remove the disc, close the tray (if any) and press ENTER to continue" usplash prompt.

So in your boot_command you need to specify noprompt after automatic-ubiquity or after the quiet option.
[/LIST]

---

