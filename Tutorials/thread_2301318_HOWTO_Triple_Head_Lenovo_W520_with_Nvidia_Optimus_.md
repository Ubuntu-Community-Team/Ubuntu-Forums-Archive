---
title: "HOWTO: Triple Head Lenovo W520 with Nvidia Optimus on Ubuntu 15.10 x64"
date: 2015-11-01
forum: Tutorials
---

### Post by dmstudzinski on 2015-11-01
Hi I'm posting this howto because maybe it will be helpfull for someone.
It can work for you even if you have another laptop.
It's first time when I can use my W520 with Ubuntu without fighting with intel-virtual-output and screen tearing with nouveau drivers.
Generally it work's out of the box (external monitors) but bbswitch is needed to support switching Nvidia off to save battery power.

I'm not an experienced Linux user. Maybe someone can improve this howto (and bash scripts).

W520 specs:
1. Intel video card: Intel i7-2860QM (with Intel HD 3000 video card)
2. Nvidia video card: NVIDIA Quadro 1000M
3. 2x Iiyama ProLite X2472HD

Nvidia Optimus enabled in BIOS.
Optimus support detection enabled in BIOS.
One monitor is connected by VGA (D-Sub) cable
Second monitor is connected with DisplayPort -> HDMI cable (it work's with Unitek DisplayPort to HDMI converter too)

**Description:**
DisplayPort and VGA (D-sub) is wired to Nvidia card so Nvidia has to be enabled (sadly) for output to external monitors.
Performance does not matter for me. Intel performance and performance of nouveau drivers are OK for me.

**How It works:**
Usually I'm working on internal LCD. In this case nvidia card is switched off. This is default state after boot.
If computer is iddle with brithness on first level (for example reading articles) indicator shows about 4-5h on my old 42t4799 battery.

If I need to connect external monitors I'm manually enable nvidia card (it enables monitor outputs).
With external monitors connected battery life drops to 2h.
Battery life on Ubuntu/Windows is very similar.
Enabling/Disabling Nvidia card forces logout so save your work before!

**Installation:**
1. Install Ubuntu 15.10 x64
I've installed Ubuntu from ubuntu-15.10-desktop-amd64.iso
I've installed Ubuntu without downloading updates (only with 'install third-party software' selected) so this howto works with packets versions from this iso file.
If this solution will stop working in future check your packets versions with ISO file.
Currently (29th of October) I have installed all updates and this solution still works.
After install you should see output on your external monitors but Nvidia is permanently powered on so battery life is very short.

2. Update packets information:
```
sudo apt-get update
```

3. Install bbswitch-dkms (for me it was 0.7-2ubuntu1 version) to support switching nvidia on/off
This command also installs dkms (for me it was 2.2.0.3-2ubuntu6)
```
sudo apt-get install bbswitch-dkms
```

4. Configure bbswitch. On boot nvidia is disabled. Before powering off nvidia is enabled (some laptops don't like powering off with nvidia switched off)
```
sudo nano /etc/modprobe.d/bbswitch.conf
``` 

file contains one line:
```
options bbswitch load_state=0 unload_state=1
```

5. Load bbswitch module on boot
```
sudo nano /etc/modules-load.d/bbswitch.conf
``` 

file contains one line:
```
bbswitch
```

6. Blacklist Nvidia drivers
```
sudo nano /etc/modprobe.d/blacklist.conf
```

add these lines at the end of file:
```
# Blacklist the alternative nvidia module
blacklist nouveau

# Blacklist the original nvidia module
blacklist nvidia
```

7. You have to update your initial ramdisk (initrd) for the changes propagate to the boot process.
```
sudo update-initramfs -u
```

8. Reboot
```
sudo reboot
```

**Installation is complete. You can use enable/disable/check script which I'm including below.**
**If you would like to do it step by step (without scripts):**
1. Test if Nvidia is powered off on boot:
```
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

```

Example output:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108GLM [Quadro 1000M] [10de:0dfa] (rev ff) (prog-if ff)


```Only Intel should have [VGA controller] at the end

2. Enable nvidia. Last command will logout you instantly! Save your work!
```
sudo tee /proc/acpi/bbswitch <<<ON
sudo modprobe nouveau

```

Test if all is ok:
```
cat /proc/acpi/bbswitch
```

Should show:
```
# 0000:01:00.0 ON
```

Test video cards:
```
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
```

Example output:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108GLM [Quadro 1000M] [10de:0dfa] (rev a1) (prog-if 00 [VGA controller])

```

Intel and Nvidia should have [VGA controller] at the end

3. disable nvidia
Switch to new terminal ctrl+alt+f1 and log in
Stop lightdm to unload nouveau driver (you can't simply rmmod nouveau because driver is in use) then:
```
service lightdm stop

```

Unload nvidia driver
```
rmmod nouveau

```

Disable NVIDIA card
```
tee /proc/acpi/bbswitch <<<OFF

```

Start lightdm
```
service lightdm start

```

**Bash scripts:**
I made bash scripts to enable/disable Nvidia card.
You can set your nautilius/file browser to ask you everytime to run or open executable file.
If you change default behavior than you can run script by double click on file and then click 'run in terminal'.
You can change default behavior by opening nautilius/files app -> edit menu -> preferences -> behavior tab -> under "Executable Text Files" choose "Ask each time"

enable.sh:
```
#!/bin/bash
# check if script is being run as root
if [[ $EUID -ne 0 ]]; then
    # script being run as normal user. rerun as a root
    sudo $0
    exit 1
fi

echo "Switching NVIDIA card ON:"

# switch NVIDIA on
tee /proc/acpi/bbswitch <<<ON

echo "Loading NVIDIA driver... Please wait until logout"

# load open source nvidia driver (nouveau)
modprobe nouveau

```

disable.sh:
```
#!/bin/bash
# check if script is being run as root
if [[ $EUID -ne 0 ]]; then
    # script being run as normal user. rerun as a root
    sudo $0
    exit 1
fi

# prevent script to be killed/stopped when user will be loged out due to lightdm stop
trap "" 1

# stop lightdm to unload nouveau driver (you can't simply rmmod nouveau because driver is in use)
service lightdm stop

# unload nvidia driver
rmmod nouveau

# disable NVIDIA card
tee /proc/acpi/bbswitch <<<OFF

# start lightdm
service lightdm start

```

check.sh
```
#!/bin/bash
STATUS=`cat /proc/acpi/bbswitch | cut -d ' ' -f 2`
ADAPTER_INTEL=`lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep "VGA controller" | grep "Intel" | wc -l`
ADAPTER_NVIDIA=`lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep "VGA controller" | grep "NVIDIA" | wc -l`

if [ $STATUS = "OFF" ] && [ $ADAPTER_INTEL -eq 1 ] && [ $ADAPTER_NVIDIA -eq 0 ]; then
    echo "NVIDIA card is OFF"
elif [ $STATUS = "ON" ] && [ $ADAPTER_INTEL -eq 1 ] && [ $ADAPTER_NVIDIA -eq 1 ]; then
    echo "NVIDIA card is ON"
else
    echo "Something wrong. Check details:"
    echo "bbswitch status:"
    cat /proc/acpi/bbswitch
    echo "Enabled adapters:"
    lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep "VGA controller"
fi

# wait for key press before closing terminal
echo "Press any key to exit"
read -n 1 -s

```

you should set files as executables:
```
chmod +x enable.sh disable.sh check.sh

```

**Known issues:**
1. There are problems with Gnome flashback (Gnome classic) with Nvidia powered on.
It works if external monitor is placed on side of internal LCD.
If I move external monitor above internal monitor then internal monitor goes black

2. I can't change right external monitor position (D-Sub connected) to be slightly lower than left monitor (displayport).
If I change the position I have strange behaviour (image1).
If both monitors are on the same vertical position then all is ok (image2)

---

