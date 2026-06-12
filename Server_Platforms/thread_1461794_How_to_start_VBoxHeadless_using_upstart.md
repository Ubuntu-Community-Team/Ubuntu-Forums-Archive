---
title: "How to start VBoxHeadless using upstart?"
date: 2010-04-24
forum: Server Platforms
---

### Post by archayl on 2010-04-24
Like the title stated :)

Anyone with experience or suggestion, please do share. I've tinkered all night with this thing. Never get the VBox service I created to start.

Here is my final code before I dried my brain.

```
# Archayl Server startup
#
# Server startup
# 

description     "Archayl Playground Server"

start on (runlevel [2345])

stop on (runlevel [016])

expect daemon

exec sudo -H -u archayl VBoxManage startvm server --type headless

pre-stop script
    exec sudo -H -u archayl VBoxManage controlvm server savestate
end script

```

Any help is greatly appreciated. And I'm trying not to use SysVinit. Thanks!

---

### Post by archayl on 2010-04-25
I've worked my way on it, but for now, I'm on to the SysVinit way of doing things.

Based on this site - [http://www.glump.net/howto/virtualbox_as_a_service](http://www.glump.net/howto/virtualbox_as_a_service). I use that script for now until I get to have the time to fiddle around more.The only thing that I changed in the script was the type of vm I want to run. Thus,

```
    sudo -H -u $VM_OWNER $MANAGE_CMD startvm "$VM_NAME" -type vrdp >/dev/null || {

```

into

```
    sudo -H -u $VM_OWNER $MANAGE_CMD startvm "$VM_NAME" -type headless >/dev/null || {

```

That's all, and it works fine. Hope this helps anybody. :)

---

