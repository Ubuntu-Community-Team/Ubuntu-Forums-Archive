---
title: "Wsl"
date: 2023-11-14
forum: Virtualisation
---

### Post by 23bl on 2023-11-14
hey, this is my first time here. I was trying to set up a wsl for a uni project and i run it some problems.
1- when i try to edit some files i get "such file or directory"/"sshd: unrecognized service"
2- i tried to install x11 apps and when I try to run for exemple xeyes I get "Error: Can't open display:"

---

### Post by SeijiSensei on 2023-11-14
Must you use WSL? Can you use VirtualBox instead?

---

### Post by MAFoElffen on 2023-11-16
Or Hyper-V, since you are running WSL2, then you should have Windows Pro. Just enable the service.

But onward. Getting ssh to work from Windows WSL takes configuration of both the WSL side, and from Windows itself. Why because it is an emulation made to appear as if it were Linux inside of a sandbox. And it is not running SystemD.

From inside WSL
```

sudo apt install openssh-server
sudo /usr/sbin/service ssh start

```
From Admin Powershell, add a frewall rule for ssh:
```

New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd) for WSL' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22

```
Create this batch file somewhere in your User directory
```

@echo off
setlocal

C:\Windows\System32\bash.exe -c "sudo /usr/sbin/service ssh start"

C:\Windows\System32\netsh.exe interface portproxy delete v4tov4 listenport=22 listenaddress=0.0.0.0 protocol=tcp

for /f %%i in ('wsl hostname -I') do set IP=%%i
C:\Windows\System32\netsh.exe interface portproxy add v4tov4 listenport=22 listenaddress=0.0.0.0 connectport=22 connectaddress=%IP%

```
Here are 3 other ways: [https://kleinfelter.com/3-ways-to-ssh-to-a-pc-running-windows-and-wsl2](https://kleinfelter.com/3-ways-to-ssh-to-a-pc-running-windows-and-wsl2)

On doing XServer in  WSL2: [https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)

---

### Post by TheFu on 2023-11-16
That error, "Error: Can't open display:" means you don't have a display server running. That would historically mean "X/Windows Server" for the X/Client (xclock/xeyes/etc) to connect and run.  This isn't unexpected for a non-Unix system.

The easy answer is to forget WSL and use Virtualbox, install the supported Linux version of you choice (Say Xubuntu 22.04) into a Virtual Machine, and use it like a full install of Linux. That works pretty well. There are lots of examples in text and videos everywhere.  You'll find much more help with virtualbox, since there are Linux versions of it too that people use constantly.

I get the feeling that the entire reason for WSL was so that MSFT wasn't completely left behind when it came to Docker containers to run servers.  It was fear on their part and they should have been afraid, so it was smart, but trying to use it for a general purpose Linux need has proven to be a not-so-great idea.

Very few people in Linux forums will be able to help with WSL issues. We don't use it.  OTOH, if you have a full VM running under any of the popular hypervisors, then we can treat nearly all issues as Linux-only and not get stuck worrying about hypvisor/WSL issues ... er ... most of the time.

---

### Post by MAFoElffen on 2023-11-16
The requirement to add an XServer in Windows is explained in that tutorial I gave a link to...

I had used WSL and WSL2 to see what it was about, how it worked, and how far I could push it. Then said, okay... Very limited. I didn't realize how far from Linux it actually is until I tried to test my 'system-info' script on it, and that pointed out just how different it really is. It is made to look like Linux, but it really isn't at all. It is, at best, "Linux like".

Just turn on the Hyper-V feature and Install Ubuntu as a VM... Everything with work.

---

### Post by mrmonteith on 2023-12-03
> **23bl said:**
> hey, this is my first time here. I was trying to set up a wsl for a uni project and i run it some problems.
1- when i try to edit some files i get "such file or directory"/"sshd: unrecognized service"
2- i tried to install x11 apps and when I try to run for exemple xeyes I get "Error: Can't open display:"

 As far as exporting display try:
```
export DISPLAY=:0.0
```or
```
export DISPLAY=127.0.0.1:0.0
```

---

