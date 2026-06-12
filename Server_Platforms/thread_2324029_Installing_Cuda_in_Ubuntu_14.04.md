---
title: "Installing Cuda in Ubuntu 14.04"
date: 2016-05-10
forum: Server Platforms
---

### Post by owen18 on 2016-05-10
I've downloaded Cuda DEB file and intend to install it on Ubuntu 14.04 terminal

i'm a noob when comes to command as the Ubuntu 14.04 is not in Gui but in command mode.

Though I did look at the tutorial of Installing CUDA Toolkit 7.5 on Ubuntu 14.04 as below but still at a loss, would the following step work if i install the DEB File using usb thumb drive or a portable HDD?

> [$ sudo dpkg -i cuda-repo-ubuntu1404_7.5-18_amd64.deb 
$ sudo apt-get update


Anyone can guide me the correct command to execute the installation as I've no idea what is the exact command for thumb drive or a portable HDD to execute the DEB File

---

### Post by MAFoElffen on 2016-05-11
This may seems a dumb question on my part, but I've learned not to assume: Is this on an Ubuntu Server Edition that is on a computer that has a Cuda capable NVidia Card?

If so, fist find the device ID and path to the file. Then mount the device. Example:
```

sudo mount /dev/sdc /mnt

```
Then insert the path to the file, within that mount point, in this format ...
```

sudo dpkg -i /mnt/PathToFile/cuda-repo-ubuntu1404_7.5-18_amd64.deb

```
Example:
```

sudo dpkg -i /mnt/Cuda/cuda-repo-ubuntu1404_7.5-18_amd64.deb

```
Is that enough info to get started?

---

### Post by owen18 on 2016-05-11
> **MAFoElffen said:**
> This may seems a dumb question on my part, but I've learned not to assume: Is this on an Ubuntu Server Edition that is on a computer that has a Cuda capable NVidia Card?

If so, fist find the device ID and path to the file. Then mount the device. Example:
```

sudo mount /dev/sdc /mnt

```
Then insert the path to the file, within that mount point, in this format ...
```

sudo dpkg -i /mnt/PathToFile/cuda-repo-ubuntu1404_7.5-18_amd64.deb

```
Example:
```

sudo dpkg -i /mnt/Cuda/cuda-repo-ubuntu1404_7.5-18_amd64.deb

```
Is that enough info to get started?

Yes is a Ubuntu Server with Cuda capable Nvidia Card

Thanks for dropping by, i'll follow your guide later

Infact have try sudo fdisk -l 

Thinking it might list all partitions on storage devices as well as USB thumb drive next mount the usb drive and install DEB file but no go  :(

---

### Post by owen18 on 2016-05-11
> **MAFoElffen said:**
> This may seems a dumb question on my part, but I've learned not to assume: Is this on an Ubuntu Server Edition that is on a computer that has a Cuda capable NVidia Card?

If so, fist find the device ID and path to the file. Then mount the device. Example:
```

sudo mount /dev/sdc /mnt

```

Is that enough info to get started?

Try the above method and gotten an error 

> Mount: Special device /dev/sdc does not exist

Pls advise

---

### Post by Bucky Ball on 2016-05-12
So you have no desktop environment on the server? If you have you could try installing Gdebi. That will install .deb files with a double click on the file. (You may need to right-click the file and 'open with ... gdebi').

---

### Post by MAFoElffen on 2016-05-12
> **owen18 said:**
> Try the above method and gotten an error 
...
Pls advise
Your have to substitute the device ID of where your machine ID's the portable device that you have the file on. In more detail , as an explanation. Your computer needs to find where your file is. Desktop has no GUI, so you have to provide where it is in your commandline.

Do this first:
```

sudo fidsk -l
sudo blkid

```
The first command will find disks and partitions that are capable of having a filesystem, that are physically aconnected to your machine. Because they are connected, does not mean they are mounted to your system. They will not be accessible by your system, until they are mounted.

So once you find the device name, then use "ls" (list) until you find the directory path of that device, to where the file is located. Mount the device to the system. Confirm the path under the mount point, so you can add it to your commandline... to install the package.  Otherwise, "dpkg" does not know where to find the file, for it to be able to install it.

Does that explain what you are trying to do?

- Locate device
 -- Mount it
- Locate file path
 -- Use file path and name in your commandline.

---

### Post by lukeiamyourfather on 2016-05-12
Are you just trying to run applications on a server that rely on CUDA? Just install the Nvidia drivers from the official repositories. If you're trying to develop new CUDA applications and need their toolkit it looks like that's in the repositories too.

[https://launchpad.net/ubuntu/+source/nvidia-cuda-toolkit](https://launchpad.net/ubuntu/+source/nvidia-cuda-toolkit)

---

### Post by owen18 on 2016-05-13
> **MAFoElffen said:**
> Your have to substitute the device ID of where your machine ID's the portable device that you have the file on. In more detail , as an explanation. Your computer needs to find where your file is. Desktop has no GUI, so you have to provide where it is in your commandline.

Do this first:
```

sudo fidsk -l
sudo blkid

```
The first command will find disks and partitions that are capable of having a filesystem, that are physically aconnected to your machine. Because they are connected, does not mean they are mounted to your system. They will not be accessible by your system, until they are mounted.

So once you find the device name, then use "ls" (list) until you find the directory path of that device, to where the file is located. Mount the device to the system. Confirm the path under the mount point, so you can add it to your commandline... to install the package.  Otherwise, "dpkg" does not know where to find the file, for it to be able to install it.

Does that explain what you are trying to do?

- Locate device
 -- Mount it
- Locate file path
 -- Use file path and name in your commandline.

Finally i'm able to display the list of the device connected to the server.

I have type sudo fdisk i or 1 instead of Sudo fdisk l (L) once i input it as sudo fdisk l (L) i'm able to see the device ID and is location under SDA but then i'm able to mount the device using "sudo mount b /dev/sdc /mnt and next is show a long list of files but when i insert the path to the file, within that mount point as follow:> 
sudo dpkg -i /mnt/PathToFile/cuda-repo-ubuntu1404_7.5-18_amd64.deb



It display no packages found matching as below screen shot



Pls advise

---

### Post by lukeiamyourfather on 2016-05-13
If the machine has internet then just download the package instead of using a flash drive. Also please see my previous post. This stuff is already in the repositories for Ubuntu and you might not even need the toolkit, you might just need the graphics drivers which include the CUDA runtime.

```
wget http://developer.download.nvidia.com/compute/cuda/7.5/Prod/local_installers/cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb
sudo apt-get update
sudo apt-get install cuda

```

---

### Post by MAFoElffen on 2016-05-16
if it has an internet connection, and you are going to cut and paste commands without modifying them to your own situation, then do as "lukeiamyourfather" advised. Simply type it the same exact commands he posted.

If not, then you really need to adapt those parts of the commands that purtain to your machine.

For example I posted a command that I told you that as an example, if the usb drive showed up as /dev/sdc, then to use that as part of your command. You imperpretted and took that literally. My second attemot at explaining that was to have you post the results of what your machine saw as attached devices and filesystem so that either we could adapt commands to what your machine saw as that USB device, or for you to be able to use that to adapt your commands. YOu again typed the commands without adapting them to what your machine sees.

So if this needs to be "literal": I have patience and can still work with that. Please post the results of the blkid and fdisk commands I ask you to do in Post #6. If you need help with trying to be able to post those results, just ask.

This may be off-subject but may be a help to you: After yuou get this installed, you may benefit from learning more about commandline structure and having to adapt things to work the way you want it to do. If you do not... Well, 1st, your chosen platform is console based. It is "all" commandline. Beyond basic configuration of your chosen platform, in just using the CUDA toolkit, the compile and run-time options depend that you adapt to *your* local environment. You need to understand what you are typing in and why. 

Next, IMHO, talking from personal experience, I would assume that if someone was installing a CUDA tool-kit, that they are going to need to understand some fundamental basics on text based logic. No matter what language they will be using, the concepts of that are the same, whether they are a programmer or as an end-user of a console based application. If not, then you might be somewhat challenged and limited. Understanding more about that is going to make things simpler, and possibly easier to understand. I go by the theory that if you understand how things work, that you can adapt those things to work for you. Just like I think a programming tract should have a class on Google-Metrics: how to ask for what you are looking for ... and how to adapt that to work for your situation. That is how a developer takes an idea and makes it into a reality. Does that make sense?

For my own curiosity sake, NVidia says CUDA supports all extensions of C to be able to use it's API, but it's doc's mainly focus on development in C++. It supports connection from other languages, such as FORTRAN, Python, JAVA, etc. It also supports connection from libraries and middleware, such as MATLAB. Being open to so many things, what are you intending to connect to the CUDA toolkit's API with? What is your intentional use?

---

### Post by owen18 on 2016-05-21
> **lukeiamyourfather said:**
> If the machine has internet then just download the package instead of using a flash drive. Also please see my previous post. This stuff is already in the repositories for Ubuntu and you might not even need the toolkit, you might just need the graphics drivers which include the CUDA runtime.

```
wget http://developer.download.nvidia.com/compute/cuda/7.5/Prod/local_installers/cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb
sudo apt-get update
sudo apt-get install cuda

```

Follow your above suggestion and choose the "try version of Ubuntu desktop" and it run smoothly but at the end of the "sudo apt-get install cuda" keep getting error as in device space not enough

---

### Post by owen18 on 2016-05-21
> For my own curiosity sake, NVidia says CUDA supports all extensions of C to be able to use it's API, but it's doc's mainly focus on development in C++. It supports connection from other languages, such as FORTRAN, Python, JAVA, etc. It also supports connection from libraries and middleware, such as MATLAB. Being open to so many things, what are you intending to connect to the CUDA toolkit's API with? What is your intentional use?

Hi MAFoElffen, thanks for your assist. Our intention is to ensure that CUDA is fully functioning as well as to run CUDA GPU Parallel Computing Benchmarks on K80 cards on a Which is something new to me. 

Just a thought, other than using CudaMFLOPS1 benchmark. What other method we can run CUDA GPU Parallel Computing Benchmarks?
Could CudaMFLOPS1 benchmark or CUDA GPU Parallel Computing Benchmarks run on gui mode (Desktop) other than using command? If be great if we can run CUDA GPU Parallel Computing Benchmarks on Gui mode

The objective is to ensure the CUDA GPU Parallel Computing Benchmarks could run smoothly on a 2x K80 cards with Ubuntu OS

So long the CUDA is fully functioning as well as able to run CUDA GPU Parallel Computing Benchmarks on 2x K80 cards, my objective has met

Kindly advise and show me the step. Thanks!

---

### Post by MAFoElffen on 2016-05-23
On on thought/Question... Yes, you can run Cuda on Ubuntu Desktop as an OS. It is the same Ubuntu Core core with GUI Layers added on.

Your Cuda Benchmarks should not vary whether the base OS is GUI based or Console based. You are benchmarking the K80's, which will only be accessed thorugh the Cuda API. 

It will take a bit more of base system memory. About 512 MB more, if you ran Gnome 3 or Full Ubuntu. What it would give you is easier filsystem mounts and a GUI based editing without having to know commandline to maneuver. 

On with your problem...
> **owen18 said:**
> Follow your above suggestion and choose the "try version of Ubuntu desktop" and it run smoothly but at the end of the "sudo apt-get install cuda" keep getting error as in device space not enough
Wait: You are not installing on a system? Because "try version of Ubuntu Desktop is not an OS Installation, but rather running on a temporary Live Image filesystem. IMHO, I don't feel you can accurately test benchmarks on a LiveCd Image. There is too much in the overhead to run benchmarks fairly. I feel if you are going to run benchmarks, then you need to be running an installed system either on metal. or as a GPU pass-through in Virtual.

Next, to explain what you did and what followed (the error), the deb package you installed using dpkg should have added one or two lines to your /etc/apt/sources.list file with the repository that contains the Cuda packages. That translates to, it gives your system pointers to be able to file the files your will need to install Cuda. The update command should have refreshed your apt cache with the  new pointers, and add pointers the new packages from that new repo. The error in installing Cuda... What exactly is that error? = Please post that error.

I see it... It told you there was not enough room in the LiveCD image filesystem to install Cuda. My recommendation would be to install Ubuntu (whatever version of) on a system, then install Cuda on that system. For testing, if you just removed all the disks on a system and took a small HDD that you could use for your test, then run your benchmarks.

I get given small HDD's for testing from a computer recycler. They feel anything smaller than xx GB's is too small to recondition and put back into one of their systems. I get those smaller drives, low level format, zero, mark verify them... These days, you could pick up a new 500 GB drive for around $40-$50. Put a drive in and play. It's just testing... and some tests you have to do on metal.

---

### Post by owen18 on 2016-05-23
> wget [http://developer.download.nvidia.com/compute/cuda/7.5/Prod/local_installers/cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb](http://developer.download.nvidia.com/compute/cuda/7.5/Prod/local_installers/cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb)
sudo dpkg -i cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb
sudo apt-get update
sudo apt-get install cuda

I have successfully download the CUDA Toolkit and have successfully install the CUDA following the above step on my server.

 Now I need to run CUDA GPU Parallel Computing Benchmarks 

Anyone could guide me the step and command? Is there anyway I could run the computing benchmarks in gui mode since i'm running a Ubuntu desktop?

---

### Post by owen18 on 2016-05-24
> **owen18 said:**
> I have successfully download the CUDA Toolkit and have successfully install the CUDA following the above step on my server.

 Now I need to run CUDA GPU Parallel Computing Benchmarks 

Anyone could guide me the step and command? Is there anyway I could run the computing benchmarks in gui mode since i'm running a Ubuntu desktop?

Appreciate if anyone could show me the step for running CUDA GPU Parallel Computing Benchmarks

---

### Post by MAFoElffen on 2016-05-25
> **owen18 said:**
> Now I need to run CUDA GPU Parallel Computing Benchmarks 
... and you ask for help in running "*it*." [COLOR=#ff0000]***But***[/COLOR] you do not describe what or who's "benchmarking suite" you have installed ... This, then, is is sort of an ambiguous question. Cuda comes with a profiler, to assess your code and look for bottlenecks. But does not come with a Benchmarking Suite, per say. It does come with code samples, of which, some are algorithms that are  commonly used for benchmarking:
> 

[LIST]
[*] Data-parallel algorithms and primitives for linear algebra operations:
[LIST]
[*]Matrix transpose
[*]Matrix-matrix multiplication
[*]Matrix multiplication with multiple right hand sides
[*]Parallel prefix sum of large arrays
[*]Any many more!
[/LIST]
[/LIST]

Of those samples, you would have to compile and run yourself. (refer to [NVidia's Cuda C Programming Guide]("http://docs.nvidia.com/cuda/cuda-c-programming-guide/#axzz49j4Bd2zD"))

Of the way you word that ("CUDA GPU Parallel Computing Benchmarks"), it reminds me of [Roy Longbottom's PC Benchmarking Collection]("http://www.roylongbottom.org.uk/cuda1.htm") and the title of his web page for those. More accepted for GPU acceleration and parallel computing benchmarking (in order to what is considered as the de-facto industry standards) is the  [Parboil Suite]("http://impact.crhc.illinois.edu/parboil/parboil_download_page.aspx") and the [Rodinia Suite]("http://www.cs.virginia.edu/~skadron/wiki/rodinia/index.php/Rodinia:Accelerating_Compute-Intensive_Applications_with_Accelerators").Follow those links and they will describe what they are, what they do, and how to use them. Both those also have are at GitHub.

---

### Post by owen18 on 2016-05-27
Encounter a new issue, after install CUDA 7.5 toolkit and when I power on the server, I was deny log in though i'm pretty sure my password is correct and when I key in the password it did not say is incorrect, beside I did wrote the password down

The screen flashes for a min after I input the password and hit enter next it just stuck on the log in screen with the username.

What could be the cause? Could it be bugs and the Nvidia where CUDA install by itself during the update and installation. Though I did try using Ctrl+ALT+F1 and it allow me to go into a terminal though I did try the command of sudo and Xauthority need sudo reboot but still no go


Pls advise

---

### Post by MAFoElffen on 2016-06-02
> **owen18 said:**
> Encounter a new issue, after install CUDA 7.5 toolkit and when I power on the server, I was deny log in though i'm pretty sure my password is correct and when I key in the password it did not say is incorrect, beside I did wrote the password down

The screen flashes for a min after I input the password and hit enter next it just stuck on the log in screen with the username.

What could be the cause? Could it be bugs and the Nvidia where CUDA install by itself during the update and installation. Though I did try using Ctrl+ALT+F1 and it allow me to go into a terminal though I did try the command of sudo and Xauthority need sudo reboot but still no go


Pls advise
Wait, you rebooted and logged in between installing the system and installing cuda right? No matters...

On boot, just past the BIOS messages, press the left shift key so the Grub Boot menu shows. Use the recovery option, to bring up the recovery menu. > At that menu, use the last option and selct drop to root prompt...
```

passwd UserName

```
Using your own user name. Reset your password. If it errors out on the user not found, then that was your problem. You could then either reinstall or create another privileged user...

---

