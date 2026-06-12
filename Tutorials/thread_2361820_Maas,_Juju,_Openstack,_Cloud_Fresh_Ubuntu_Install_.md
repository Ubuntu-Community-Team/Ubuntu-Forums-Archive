---
title: "Maas, Juju, Openstack, Cloud Fresh Ubuntu Install Guide"
date: 2017-05-21
forum: Tutorials
---

### Post by ksmacd on 2017-05-21
Hi guys,

Im kirk i would just like to share what i have achieved as sharing is  caring and in the open source world sharing what you have learned is key  for the open source world to thrive.

Anyway i have created a guide here which will give you instructions from  building a cloud from scratch which including installing ubuntu,  installing maas, installing juju, creating a cloud, creating the juju  controller and finally deploying your cloud.

I got this going then what i did is remember each step and code then  started from scratch again and wrote this guide whilst doing each step  on the machines so this guide is complete and correct.

[COLOR=#ff0000]PLEASE READ EACH SECTION BEFORE YOU TRY IT READ IT AGAIN THEN READ IT AGAIN SO YOU FULLY UNDERSTAND WHAT IT IS YOU ARE DOING BEFORE YOU DO IT.[/COLOR]

Ok lets go

                                              ```
Maas, Juju, Cloud, Openstack, Machine Scaling guide
```

Ok guys im writing this guide because i have spent many many hrs,  starting from scratch going one step forward 10  steps back having to reinstall fresh builds because i messed something  up honest truth i properly reinstalled a good 30 times all because there  is not a complete guide to get this done or there is a misconception on  getting it done there are many guides but not complete from scratch to  finish so u have to pull a bit from here and a bit from there this  is where the misconception comes into play see there are different  methods to installing landscape or autopilot or getting a cloud going  well problem is if you follow the guides and take a bit from here and  there well you get conflicts when getting it going and have to re  install from scratch

I have taken all the bits and put it together and made a functional  scalable cloud dont ask took 3 weeks but for you this can be  accomplished now in a around 12hrs if you follow this guide

I can not stress enough that this is only a test setup and it is  designed to teach you how to get a production one done this is to teach  you the process i strongly advise to not put these configs in  production one once you know how to set up a cloud and everything you  can set your own ip addresses folder locations and file names ports etc  because you know the steps to make a production server cloud as you have  just learned

if you keep the ip, ports, file names the same in a production  environment you are leaving you self open for hacking as this guide is  on  the web now and hackers can use this info to infiltrate your system if  you keep the production environment the same as the test one

[COLOR=#ff0000]YOU HAVE BEEN WARNED[/COLOR]

Ok i did get all this going on 1 sever with virtual boxes each with 1 cpu and 4.5 ram dont do that its as slow as anything

this is the set up i have

2 actual physical machines not virtual machines actual machines each  with 8 cpu and 32 ram hard drives i would say about minimum 160gb hard  drives in both we will get onto the vboxes later but this is what you  need minimum to get this going also we are going to install all of the  cloud systems into vboxes this is so they can be backed up easier and  moved to a new machine with ease if there was a hard drive failure or  machine falure so you can get your cloud back up with ease as a fail  safe. As we are using 2 machines if you want to move each vbox over to a  physical machine for some oomph you would have to make the new machine  install vbox then just add the vbox and adjust the cpu rams but then you  will have to manually secure the machine as it will not be added to the  cloud

The juju cloud im sure there is a charm that can sort out stuff like that for you but i have not got that far ahead

If you have actual machines around then you will need 6 machines if you dont then 2 is okay we will use 2

Also you need network switch goes with out saying if you are using 6  machines, you can use your router if using just 2 but i doubt that

Make sure your ether cables are a minimum cat 5 try for cat 7 as its a  lot faster or if like me upgrade your system network switches and  everything to fiber optic speeds are crazy

[COLOR=#ff0000]so just to make sure vbox setup 2 machines or if you have actual machines then 6 machines[/COLOR]

when you want to build an actually production cloud use 6 physical  machines as they will be in the cloud and will be protected or you could  just install webmin on the new machines and still keep controllers in  vboxes
thats upto you but that is not covered here as this is just a teaching guide to get you up and running.

[COLOR=#ff0000]right we need our 2 machine setups we need a minimum of 8cpu and 32gb ram in each
our 6 machine setup needs minimum 2cpu and 4.5 ram[/COLOR]

Do not try to install autopilot or landscape they argue that you need  8cpu and 8ram in each machine which is not true and install will always  fail leaving you scratching your head.

This guide does not cover landscape or autopilot this is a  manual setup, config where we make it become like a autopilot cluster so  they are not needed to be honest you just have to follow this guide and  you will get everything going and to be honest autopilot, landscape  work with maas to power machines on with wake on lan if you are using  the vbox setup or 6 cluster setup there is no more wake on lan actually  in maas no more

there is other wake up things like virsh but i couldnt get it to work, i  will work it out thou and post at another date. So landscape and  autopilot allways fails because it dont turn machines on i tried to use  autopilot and landscape with the manual power type but that fails as well  as the machines have to be powered on in a certain order and time  within sync of the landscape in order to install in the correct sequence  so it always fails this is why we do it the manual way using the juju  controller but we will get on that a bit more.
The above landscape stuff took me around a week to figure out exactly  why it fails etc and how to over come this. This is why we manually do  it  :smile: 


[COLOR=#ff0000]Do not follow this section if you are using 6 machines[/COLOR]


ok we need to set both machines up within the bios we need to set do not  boot pxe as they are the main 2 nodes that will host everything we also  need to turn visualization on and set the boot order to usb, hardrive,  network


[COLOR=#ff0000]Do not follow next bit if your using 2 machines skip to next section[/COLOR]


If you are using 6 machines then they need to be setup like this in bios

1 needs to boot from hardrive first and only needs 1 hard drive can be  20gb we will call this maas machine this is the main machine and needs to  have 2 ether cables plugged in

1 needs to be boot order from lan,pxe then hardrive, only needs 1 hard  drive can be 20gb [COLOR=#0000cd]we will call this machine juju controller[/COLOR] only needs 1  ether cable

1 needs to be boot order lan,pxe then hard drives only needs to be 2 x 20gb [COLOR=#0000cd]we will call this openstack0[/COLOR]  needs 2 ether

3 needs to be boot order lan,pxe then hard drives do not set the hard  drive boot order as the open stack installer swaps them around 6hrs  it took me to work out what whent wrong and work that bit out but we  will be changing the order later on, these 3 machines need 2 hard drives  each 20gb and 2 ethers plugged in

[COLOR=#0000cd]the machines need to be called openstack 1 to 3[/COLOR]

we call the machines like that so we can easily recall what machine is doing what

i use ubuntu desktop as the base this is because it has a gui and makes  things easier as you can see what you are doing trust me use this as a  base as i would imagine some of you are so used to windows using the  termi all the time will drive you nuts

just discovered open stack randomly picks a node so have 2 ethers in openstack 0 - 3 just incase it picks by mistake the wrong node with one ether and install fails

[COLOR=#ff0000]Complete this step if using 2 machines[/COLOR]


so create your ubutnu desktop usb pen and install on both machines
i must stress setting up security for these to machines will not be done by the cloud so you will have to do these manually.
Thats down to you to do as this is cloud setup instructions.


[COLOR=#ff0000]Complete this step if using 6 machinces[/COLOR]

Install ubuntu desktop on [COLOR=#0000cd]machine called maas

[/COLOR][COLOR=#ff0000]
Steps for both setups[/COLOR]

once installed on both setups we shall do the following

we need to go to system settings and go to screen lock and turn off very  annoying to keep logging in every 5 min whilst we are waiting for  upgrade and stuff

then we go to 

software and updates and click on source code enter password and select  main server then move tab to other software and select canocial software  and select both do not select cd rom

close then do not click refresh

we need to open a terminal by pressing ctl, alt and t

we type in

```
sudo apt update
```                          (this will ask for password enter it)

once its finished enter 

```
sudo apt upgrade
```

do not reboot yet enter the following in termi

```

sudo apt install unity-tweek-tool
```
```
sudo apt install putty
```
```
sudo apt install gksu
```

do not reboot yet go back to software updates and select additional  drivers and install as appropriate please in stall as if you dont might  make vbox crash lmao took me a while to work out why that kept  happening.

now reboot

[COLOR=#ff0000]only do this if you have problems with the resolution reboot the  machine a few times to check im using a kvm swicth on a 32" tv every  other boot my screen res changes from normal to some weird layout to  over come this[/COLOR]

in termi type

```
sudo nano /etc/default/grub
```

find```
 #GRUB_GFXMODE=
```                         and replace with



```
GRUB_GFXMODE=1024x768x32
```                            make  sure you remove the # symbol aswell and add the next code under it
```
GRUB_GFXPAYLOAD_LINUX=1024x768x32 
```

once you have done this press ctl and x it will ask you to over right type y then just press enter twice

then in termi type

```
sudo update-grub
```

then reboot

[COLOR=#ff0000]i must stres that screen res works with my tv u will have to find out and replace with what your tv does best

if you mess it up and you cant see cos its to wide or so reboot with usb  pen install but click on try now this will let you in to change the  size but you will have to google on how to mount the folder etc so you  can accomplish this anyway[/COLOR]

once rebooted res should be sorted

[COLOR=#ff0000]Steps for all from now on just keep following
[/COLOR]
go launch unity tweak tool and move the side bar to the bottom

Ok what we are all here for the main setup

ok now we get on to installing maas in termi type

```
sudo apt install maas
```

once this is installed in termi type

```
sudo maas createadmin

```

enter your user name you want to use and password when it says about ssh keys press enter we will that bit in a bit
[COLOR=#ff0000]
NOW THIS NEXT BIT IS VERY IMPORTANT AND I WILL EXPLAIN WHY[/COLOR]

ok maas acts as a dhcp server which means you need to disable the main  routers one but wait do not do it untill i say and you understand this  section as other guides for get to tell you this part and it took about a  week to find out whats going on why its going on and how to sort with  the kids saying dad the internet is off again lmao but il explain now.

ok when you disable the routers dhcp and set maas up as the dhcp this  routes all traffic wireless ethernet everything to you maas server lmao  if the maas server is of it will break the connections to all devices  and you will have no net. My server is on so its ok to route all traffic  but if the maas server goes of it breaks the net.

you have to do the next steps for maass to work and cannot get all   other dervices to work after theese steps but as i have worked this out  internet should be off for no more then 15min unlike on off for a week  cos i didnt know what i was doing lmao

[COLOR=#ff0000]ok go to network top right click on connection info this is important  you do this so we can work out your router addresses and change them in  the following file as yours will be different then mine[/COLOR]

write down

the following mine dns server address and gateway

mine looks like this

```
gateway 192.168.0.1
dns-nameservers  194.168.4.100
```

now go to your webpage and type in what ever the gatway address is mine  is [COLOR=#ff0000]192.168.0.1[/COLOR] and login if you have not already changed the login  details then shame on you have a lot to learn lmao 1 word wps reaver  pixy dust less then 30seconds any way your login details should be on a  sticker to the router.

anyway find dhcp and turn off ok now there is no net dont panic its not broke

go to termi and type

```
sudo nano /etc/network/interfaces
```

delete everything and copy and paste the following be advised you need  to change a couple of things before you save them but il tell you in a  moment

```

# interfaces(5) file used by ifup(8) and ifdown(8) (local host loop)
auto lo
iface lo inet loopback

# outside network
auto [COLOR=#ffa500]enp0s9[/COLOR]
iface [COLOR=#ffa500]enp0s9[/COLOR] inet static
        address 192.168.[COLOR=#ff0000]0[/COLOR].10
        netmask 255.255.255.0
        broadcast 192.168.[COLOR=#ff0000]0[/COLOR].255
        gateway [COLOR=#00ffff]192.168.0.1[/COLOR]
        dns-nameservers  [COLOR=#ee82ee]194.168.4.100[/COLOR]


# maas network
auto [COLOR=#008000]enp0s8[/COLOR]
iface [COLOR=#008000]enp0s8[/COLOR] inet static
        address 10.1.1.100
        netmask 255.255.255.0

        post-up iptables -t nat -A POSTROUTING -o [COLOR=#ffa500]enp0s9[/COLOR] -j SNAT --to-source 192.168.[COLOR=#ff0000]0[/COLOR].10
        post-down iptables -t nat -D POSTROUTING -o [COLOR=#daa520]enp0s9[/COLOR] -j SNAT --to-source 192.168.[COLOR=#ff0000]0[/COLOR].10

```

################################

okay so when you wrote down your network you need to change the following

 address 192.168.[COLOR=#ff0000]0[/COLOR].10  here you change the [COLOR=#ff0000]0[/COLOR] the no left of the last . from last no to the  same in the  gateway no you wrote down        
        netmask 255.255.255.0
        broadcast 192.168.[COLOR=#ff0000]0[/COLOR].255  same here you change [COLOR=#ff0000]0 [/COLOR]same no as gateway
        gateway [COLOR=#00ffff]192.168.0.1[/COLOR]      so if you gateway was [COLOR=#00ffff]192.168.1.1[/COLOR] or so you change gateway to that what you wrote down
        dns-nameservers  [COLOR=#ee82ee]194.168.4.100  [/COLOR]if dns was [COLOR=#ee82ee]193.168.2.1[/COLOR] or so you do the same you change it to what you wrote down

also open a new termi and type ```
ifconfig
``` this will give you you network card name

so if its [COLOR=#008000]eth0[/COLOR] or so or [COLOR=#008000]ens3[/COLOR] what ever has the lowest no you change the green code to what this is called here in ifconfig so 

[COLOR=#008000]enp0s8[/COLOR] becomes to what ever yours is called there is 2 to change but they are colored so you know what to change
[COLOR=#ff8c00]enp0s9[/COLOR] you do the same with the other the higher no there is 4 of those to change

also at the bottom dont for get to change the 2 post tables ip second  from last digit which is [COLOR=#ff0000]0[/COLOR] to the same as digit left of the last . from the gateway code

once you have successfully configured this press ctl and x press y then enter

the fun does not stop there il get to that

now reboot

once you are now rebooted chck you can access the web with firefox if  not you made a mistake go over the above steps make sure every time you  alter the config reboot

[COLOR=#ff0000]service network-manager restart is conceiving it sometimes temps  fixes then when you reboot previous setting revert always reboot that  way you know the current settings work[/COLOR]

Fixing other devices that have no Internet or or do
now maas is acting as a dhcp if it gets turned off your wifi or other  ether connected devices will have no Internet as all traffic is routed  through you new sever.

you have to manually select a static ip on the device but punch in the  gateway and dns you wrote down and give it a static ip from make sure  its the same as your gateway you wrote down but change the last digit to  like 11 then the next device you set up 12 and so on

turn you off your maas sever and check to make sure your other devices  work whilst you server is if if they do then your all good.

i would like to point out maas is you main server if you are building  more clusters away from this cluster at a different location just set up  a server as a dhcp server and route all traffic to this main cluster by  simply typing in at this server firefox page what is my ip this will  give you your external ip address then just add that to the above file  as the external ip this will route any new clusters you have to this  cluster make sure you service provider is giving you a static external  ip thou.

But as it stands we are not building a external cluster so forget about  the bit i said i would like to point out unless that concerns you.

If for any reason you would like to revert network settings go back to your router login in turn dhcp back on

type in termi

```
sudo nano /etc/network/interfaces
```

delete everything apart from

```
# interfaces(5) file used by ifup(8) and ifdown(8) (local host loop)
auto lo
iface lo inet loopback
```

then press ctl x save it then reboot everything is reverted

Ok next

in termi type

```
sudo dpkg-reconfigure maas-region-controller
```

and change to

```
10.1.1.100
```

save

then termi again type

```
sudo dpkg-reconfigure maas-rack-controller
```

and change to

```

[http://192.168.[COLOR=#ff0000]0[/COLOR].10/MAAS]("http://192.168.0.10/MAAS")
```

make sure you change second from last [COLOR=#ff0000]0[/COLOR] to the the didget to the one you  changed in the interface file and MAAS is spelt with caps

now save
              
in fire fox type

```
10.1.1.100/[COLOR=#ff0000]MAAS[/COLOR]
```            Make sure [COLOR=#ff0000]MAAS[/COLOR] is Spelt [COLOR=#ff0000]MAAS[/COLOR] and not maas or it wont work

it will complain about ssl key just add acception and continue its down  to you to work out and secure your system with ssl security i must advise  make sure you do

once logged in on the first page under dns forwarder type

```
8.8.8.8
```

then move down and make sure the images section says yes before going to the next page

ok on the next page it asks for ssh key

ok in termi type this but[COLOR=#ff0000] DO NOT AND I REPEAT DO NOT DO IF YOU ARE UNDER  ROOT[/COLOR] this is for the more ileterate linux you will know what im talking  about this will cause problems for the key

oh first we need to press the files folder then press ```
ctl and h
``` if done  right you will see some folders or files with a . infront of them if you  see this proceed create a folder called [COLOR=#ff0000].ssh[/COLOR]

now in termi type

```
ssh-keygen -t rsa
```

it will ask you where to save the file copy exactly how it is spelt next to it ie```
 /home/yourname/.ssh/[COLOR=#ff0000]id_rsa[/COLOR]
```

but change the```
 id_rsa to
``` ```
[COLOR=#ff0000]maas_rsa[/COLOR]
```

this is so you know what key is for what

now you have made the key go to that folder

file folder press ```
[COLOR=#ff0000]ctl h[/COLOR]
``` to view hidden files then go into .ssh then open  up ```
[COLOR=#ff0000]maas_rsa.pub[/COLOR]
``` with gedit and select all and copy now go back to  firefox

select
upload keys source then paste into the box and upload

then select go to dashboard

go to subnets and select

the one that says 192.168

then move it over to fabric 1 no need to save just click subnets again

then click on 10.1.1

and add the following to the gateway and dns

```
10.1.1.100
```

then click subnets again

now the the untagged vlan next to fabric-0 press make sure you press that and not the other

press provide action and then provide dhcp

cool so far so good still lots to go

now go to node select controller go to the network devices and make sure

the lower no network is set to fabric 0
select sub net 10.1
ip mode is set to static and you give an ip address of 10.1.1.100

then the other network you the higher one you select fabric 1
sub net 198.168
ip mode static but put 192.168.0.10  remember to change the 0 to the number  you changed it to in the network file you added and save

[COLOR=#ff0000]if they dont change to static repeat sometimes you have to do it twice to take affect dont as why[/COLOR]

ok do this if you are doing the 2 server install if doing 6 skip this whole vbox setup

in termi type

```
sudo apt install virtualbox 
```on both machines

on machine 1 called maas

we need to make 2 vboxes

with the following setup

```
1 box named Juju controller
1 box named Openstack0
```

openstack0 needs 2 20gb drives named openstack0.qed and openstack00.qed
it also needs to network cards enp0s8 and enp0s9

Juju controller needs to have the following settings
name it Juju controller and select linux ubuntu 64bit
8gb of ram
create hard drive qed format and select 20gb

once made click device and select settings
under general select bidirectional for keyboard and mouse
under system select 2 cores and change acceleration to hyperv also move  network and select to boot first then harddrive to boot second
go to network select bridge and select lower no
[COLOR=#ff0000]
Please and i stress make sure all yor network interfaces you select advanced go to promiscouse mode a select allow all on all virtual boxes network cards other wise like me i missed one and could understand why one of my boxes kept failling when installing the openstack bundle[/COLOR] 

save

power up machine and check if it boots up with the new lan dhcp boot you  should get a ip like 10.1.1.101 or so this is good this means you set  up maas and vbox correctly if this does not do that then something is  wrong then you need to go and check above cos something is wrong.

ok make the other vbox with exactly the same settings as above and name it
```

Openstack0
```

do the same power up then check then power off

We need to do the same on the other machine named maas1

but we need to make 3 vboxes

all with normal settings as above but all 3 need an extra hard drive created
go to the box settings and select sata then create hard drive with qed  but name them like ```
openstack 11 for opnstack1 or 22 for openstack2 or 33  for openstack3
```

we also need to make another network interface also bridged but this one  we select the higher device no so we have to 1 with lower connection  and the other with the higher one

make sure network boot is first and power up and check to see if it boots from dhcp now power then all down

[COLOR=#ff0000]#############################################
##################################################  ######
##################################################  #############[/COLOR]

Hi 6 node guy this bit is for you welcome back

ok name each machine
```
1 maas which you have ubuntu installed
2 juju controller
3 Openstack0
4 Openstack1
5 Openstack2
6 Openstack3
```

no device 1, 4, 5, and 6 needs 2 ethers plugged in and no's 2, 3, needs 1
no device 4, 5, and 6 needs 2 hard drives

device 1 needs to be hard drive disk boot first turn network boot off

all the rest needs to be network boot then hard drive now you have maas controlling them

now make sure maas machine is on and power up juju machine if when  booting it up and it boots via dhcp and and you see a ip address of  10.1.1.100 all good you have been paying attention and have done it  right so far if you dont you have to go back and find out what you have  done wrong and fix it.

Ok power down the juju machine.

[COLOR=#ff0000]
Steps for all to do[/COLOR]

ok go to webpage ```
10.1.1.100/MAAS
``` from your browser to access maas gui

go to nodes and if there are any under machine delete them as it will save confusion

power on the juju machine wait about 3-5 mins then it should appear if  it dont go to the machine look at the screen if it says something like  bad things are to come you messed something up in the interfaces but if  you followed this guide you should be ok.

ok

click on the machine it will have a funny name with .maas after it once  you clicked it we need to change the name click on the name top right  and name this one

[COLOR=#ff0000]Juju-Controller[/COLOR]

scroll down to power type this for is a bit of a sore subject maas took  away in maas2.0 power control wake on lan for some reason and virsh is a  nightmare spent a week trying to get power mode to auto with no success  i will do it but might take some time i also tried this using vmware  boxes but still not either so i will post once i work it out but for now  select 

[COLOR=#ff0000]Manual power
[/COLOR]
save

now top right under action select commission and power on juj machine  after about 5 min it will say ready and display info about it

you need to scroll down to the devices interface and change the device to static and give it an ip of 10.1.1.101

this makes it so it keeps the same ip in case you need to ssh into it


ok back to termi

```
sudo apt install juju
```


now create a file called private-cloud.yaml and paste this into it


```
clouds:
   maas:
      type: maas
      auth-types: [oauth1]
      endpoint: [http://10.1.1.100/MAAS](http://10.1.1.100/MAAS)

```

save to home folder

then in termi type

```
juju add-cloud maas /home/your user name here/private-cloud.yaml
```

then type

```
juju update-clouds
```

if like me devs and u installed juju under root or there is a permision problem

type ```
gksu nautilus in the termi
```

when folder opens press ```
ctl h
```

go to /.local/share/juju and select public-clouds and change owner from  root to yours lmao this is why i said dont do anything on the root  account

ok we now need to add credentials

type ```
juju add-credential maas
```

type a user name you wanna use when it asks for auth key go to firefox  then go to the maas gui which is 10.1.1.100/MAAS which you have already  booked marked right

then select your name top right and select maas key and paste it in the  termi when it asks you for the auth the code is blank but its there make  sure you press no key other then enter

cool we are getting there

ok in terminal type

```
juju bootstrap
```

select ```
maas
```

and call the controller ```
juju
```

this will make the machine on the fire fox tab maas gui turn from ready to deploying

now power on the machine called juju and do nothing untill it goes from deploying to deployed

and your termi bar has gone back to user this take  about 10-15 min so be patient


once this is complete type in termi

```
juj gui
```

this will redirect you to your now cloud controller remember to book mark the page

```
juju show-controller --show-password
```

this will give you you user name and password if you have got this far  well done you are almost done you have the tool now installed to deploy a  cloud :smile:

right now we need to power each other machine up and process them the  same as before comission them but do one at a time or you will confuse  your self the ones with 2 interfaces keep the same as before but the  other interface we will set that to fabric 1 but unconfigured

name each one as they are for each machine and get them in a ready state then i will show you how to deploy the cloud

once we are all open stack machines are ready and juju machine is on login into your juju gui which you booked marked

click on controller and select manage 

click on view bundles and select openstack base

[COLOR=#ff0000]i would like to point out that opoen stack is just a basic cloud if you  want a full blown scalable infratructure you need to install the  kubertenes bundle then openstack but kubertenes requires 9 machines plus  1 for maas[/COLOR]

now you need to configure each bundle once its on the ready to deploy  page the relations part is key make sure you click the relations for all  charms, and set some key info or it will fail. but just read up in the  gui yyou booked marked all the info is there

ok now once you have set it up to the required settings click deploy go  back to your maas gui and you will each machine turn from ready to  allocated to deploying once it goes to deploying power on that machine  make sure you do it in the correct order

after about 5 mins all your machines will be on and they will be installing a basic cloud infrastructure.

[COLOR=#ff0000]keep checking the maas gui to check to see if the machine goes to  deployed if it does well done your cloud is installing if not you and it  fails you have to delete all charms by destroying them and re doing it  took me 2 tries to do this.[/COLOR]

I would like to point out on vboxes it takes along time for all the  infrastructure to deploy so be patient the guys with 6 nodes i dont  think yours will take too long.

Once its deployed you can check the status on your juju gui and click on  the particular charm and if its the dashboard or something it will give  you your address and stuff.

if you do need to redploy you have to select openstack 0 - 3 and select  release never [COLOR=#ff0000]never release juju[/COLOR] or when you try to install cloud it  might wipe juju then you have to bootstrap again

your on your own from now lol i got you this far i doubt many have got  this far lmao but its down to you now go on have a look see what you can  do go explorer and remember sharing is caring.

I will provide full support for these instructions but if you follow the guide you will need no help, but im here to help [COLOR=#ff0000]Please be advised i can not offer advise other then this guide[/COLOR]

Kirk
The bricklayer who never gave up.

---

### Post by ksmacd on 2017-05-22
I will over the next few days sort out some pictures to accommodate the above and will give a little show and tell about actually deploying charms and bundles as i have found that my self to be a bit tricky think i have that bit sorted it and worked it out and i will share over the next few days

---

### Post by ksmacd on 2017-05-22
Here  are a few pictures of the end result once everything is deployed and setup and openstack is installed

This step can be acheived by typing in the termi

```
juju:admin/default
```

then

```
juju status
```

[ATTACH=CONFIG]275233[/ATTACH][ATTACH=CONFIG]275234[/ATTACH]

then this will be shown on the juju gui

[ATTACH=CONFIG]275235[/ATTACH]

i will do a little guide in the next day on actually how to use the juju gui and add to this thread as at first it is confusing but i will take the hard work out for you

---

### Post by terryng2 on 2017-09-01
Dear Kirk,
Thank you so much for your guide. I wonder if you could share the part of accessing the Openstack Dashboard (Horizon). What is the username and password to horizon please?

Regards,
Terry

Dear Kirk,
Thank you so much for your guide. I wonder if you could share the part of accessing the Openstack Dashboard (Horizon). What is the username and password to horizon please?

Regards,
Terry

I figured out how to access the horizon. In the configure section of Keystone, changed the randomly generated admin-password to your preferred one, save settings and commit changes. The dashboard should be accessible with username=admin and password="the newly updated one". Thanks!

Terry

---

### Post by ksmacd on 2018-03-03
sorry i completely forgot about this thread lol

did you get the maas and juju setup to work it looks like you did as you was able to login into horizon

i kind of boycotted this setup as the energy consumption was of the chart and the noise the servers was making was silly as this was a home production i just did it as a learning curve lmao

i also messed around with onecp which is okay for vms on a large scale but you can not scale the resources like cpu and ram across multiple servers so you are limited to how many vms you can have on each server.

I'm currently trying to get a system setup which is scalable, runs a diskless windows environment and boots from a iscsi disk on a Linux nas system in my free time as i want a cloud based client system which i host for my business iam launching next year which will allow for expansion and is easier to control from one system

any ideas any one or point me in the right direction

---

### Post by ksmacd on 2018-03-03
i think iam going to give this another bash with the whole maas and juju setup in a vm environment as before i knew nothing about iscsi or nas and i think maas and juju has a whole lot of potential with cloud based scalability as i want to be able to scale the whole environment as the business grows and i prefer Linux as a main server and as a os over a windows environment but to the employees Linux to most is completely alien so windows on the client should be a must

---

### Post by ksmacd on 2018-03-03
i will give it a shot and post my findings once i discover them

---

### Post by ksmacd on 2018-03-05
Hit a little snag, the setup I did here was on some ex fb servers I boycotted them as the energy consumption was silly I recall like £10 a week having 4 servers on for a week which is stupid just too learn on

And you couldn't add vr graphics cards so running apps like cad was a no no

So I upgraded my system to a single pc with a nas just to cut costs down because the old setup was 4 servers a kvm switch, a network as it a fiber network switch a San and a San filler.

Problem I have now is my new setup only has one nic and is not iscsi compatible

I have ordered a dual ether iscsi card when it comes I will continue with this project and update on it's progress

---

