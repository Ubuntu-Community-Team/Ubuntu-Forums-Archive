---
title: "Help me understand file permissions in and out of my containers."
date: 2016-04-26
forum: Virtualisation
---

### Post by Plecebo on 2016-04-26
I'm learning as I go about LXD unprivileged containers in 16.04 and I have some questions. 

I have a directory on my host that I want several containers to have write access to the directory. 

Using LXD when i create an unprivileged container the root user of the that container shows on the host as uid:gid 100000:100000 and the default first user (ubuntu) is 101000:101000 so far this seems consistent, no matter how many containers i setup each has a root user with id's on the host of 100000:100000 and ubuntu user with id's on the host of 101000:101000

I've been playing around with permissions on the directory on the host (lets call it /vm/Downloads) to make it available for writing to the ubuntu user in the container. To compound the issue various processes installed on the container will have uid:gid different than the ubuntu user, and those processes I want to have write access as well. The processes do some reading, organizing, renaming processing etc on the files and I want them all to have read/write access to the files that processes from other containers may create. 

My files are shared from the host to each container in this way: 
```
lxc config device add container1 Downloads disk path=/mnt/Downloads source=/vm/Downloads
```

One way i got it to work is make the permissions on the directory very open (on the host)
```
chmod 777 /vm/Downloads
```
This is the easiest way, but I don't know this is the best way, or what I want. I'm worried about having this folders permissions wide open like this.
Another option would be to use NFS and do it over the network, controlling permissions via NFS. I'm hoping to keep the access to these files as fast as possible and would rather not send this all over the network unless that was the only way. 
I THINK the right way is to configure groups on the host that include the uid's of the accounts in the containers and give the proper permissions to that group. This is what I would love to figure out how to do, but when i tried I couldn't add uid 100000 to a group on the host... because it doesn't exist. 

Am I on the right track with this? Is there a way to add the mapped uid's to groups on the host? 

I'm newish to this unprivileged container business, so if i'm way off track please let me know. :)

Thanks for any help anyone can provide.

---

### Post by MAFoElffen on 2016-04-26
Permissions ... Think about least-privilege for system, filesystem, share-- precedence and inheritance.

Permissions by precedence go by system, then filesystem, then whatever fileshare type (Samba, NFS, ACL). So if a user or group does not have system access/permissions, they will not get anymore from anywhere else. That is the highest they will have; their limit. If a user or group has permissions in system, then they can have filesystem permissions, what ever restrictions will be the limit. Then NFS permissions will add limits on those... 

It does not go the other way. If someone using an NFS share want to access a file, they have to already have those filesystem permissions and system permissions.That make sense so far?

Next is owner ... file and directory "owner" affects those permissions in some ways, in some places...

When giving out and assigning permssions on a share, whether local or a network share, calculate the least amount needed for your users to be able to do what the need to do, 

Permissions are assigned by user | group | world. The bit fields for that are 10 bits long, first being if it is a directory or not, 3 bits for the user permission, 3 for group, 3 for user.. So "-rwxrwxrwx" would be 777. 

Better if you set to 660, which would translate to "-rw-rw----" ... then do a chown of userName:GroupName. The precedence goes backwards (other:group:user), collasping on each other, in that order. So if that user, you don't care about anything else. If in a group that has permissions, you don't care about other, etc.

I set share permissions group, then set a individual users as a member of that group. Easier to manage that way. 

Your other question, a Local mount is faster that a network share. But on metal, I usually setup a storage controller, with network shares configured pointing to where they are on that storage controller. That way it centralizes where I have to go to manage that, That would be a larger scale that a NAS, but the same concept. I use fiber for my servers on their own subnet, to my storage controller. Now think the same in virtual networking ... use an internal net to tie them together,. Then when it is accessing shares, that traffic does not affect your other networks... right?

---

