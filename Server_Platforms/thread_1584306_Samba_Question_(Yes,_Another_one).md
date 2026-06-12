---
title: "Samba Question (Yes, Another one)"
date: 2010-09-29
forum: Server Platforms
---

### Post by WhiteElephant on 2010-09-29
I am trying to put together a Samba server running as a primary domain controller.

I can't find a tutorial which specifically relates to Ubuntu 10.4 and a lot of the tutorials on google differ quite a bit.

# Install Ubuntu 10.4

# Set static IP address
sudo apt-get update

# Update packages
sudo apt-get upgrade

# Install samba
sudo apt-get install samba


Now for the hard part. Forget about the shared drives for the moment, I am only interested in getting the domain controller working with Vista Business.


# Create directories
mkdir /home/samba
mkdir /home/samba/netlogon
mkdir /home/samba/profiles

# Samba config
```

[global]
workgroup = WORKGROUP
netbios name = SAMBA
server string = Samba Ubuntu

[homes]
comment = Home
valid users = %S
read only = no
browsable = no

[netlogon]
comment = Network Logon Service
path = /home/samba/netlogon
admin users = Administrator
valid users = %U
read only = no

[profile]
comment = User profiles
path = /home/samba/profiles
valid users = %U
create mode = 0600
directory mode = 0700
writable = yes
browsable = no

```


Q1.
Is it necessary to have [netlogon] ?

Q2.
Is it necessary to have [homes] if all the user's data is stored in [profile] ?

Q3.
Is it not better to have the user profiles stored within the user's unix directory. For example: /home/user/profile/ ?

Q4.
Is it necessary to have the "add machine script" ?

Q5.
Is it necessary to map domain groups. For example: "net groupmap modify ntgroup="Domain Admins" unixgroup=root" ?

---

### Post by WhiteElephant on 2010-09-30
Bump
 
 
No-one can't help me with this?

---

### Post by kinitsu on 2010-09-30
I have not messed with normal workgroups, I have just recently got samba going for my AD though if you was my thread am having trouble with.... anywho, as for you, first priority is to get the [global] configured and samba talking with your workgroup then I would worry about the other smaller settings. Also, as a side note, is your linux box's name SAMBA because from what I have come to understand your netbios name is your computers name, or domain name if you are hosting the domain form that computer.

As for tutorials, all flavors of linux are very similar when it comes to Samba, you can pretty much use any tutorial, the only differences you may experience is shell commands but it is easy to find similar commands for your flavor of linux. I have manged to configure samba using fedora and centos tutorials.

---

