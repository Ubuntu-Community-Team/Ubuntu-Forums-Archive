---
title: "set the path seen on client of nfs mount"
date: 2014-01-11
forum: Server Platforms
---

### Post by techiebiker on 2014-01-11
Am an nfs and mount noob.

Have reached the point am using more than one Ubuntu computer regularly. Would like to share files between them and control the path the shared files appear in on the clients.

Goal: each client sees the server share(s) at

/home/username/network/

I have the nfs v4 server set up. And share the files and can read/write them from each client. However each client sees the files at...

/home/username/network/**srv/nfs**/

On the server /etc/exports contains...
/srv/nfs  *(rw,sync,no_wdelay,no_subtree_check)

On the server the actual files are in...
/home/username/

To run nfs and mount the files on the client I do the following (will get to automation later am still at the stage want to be very familiar with the steps to make it happen)

On server
1) sudo mount --bind /home/username /srv/nfs
2) sudo service nfs-kernel-server start

On the client
1) sudo mount -t nfs -o proto=tcp,port=2049 server:/ /home/username/network

And I end up with the contents of the nfs share found on the client at...
/home/username/network/srv/nfs/

And what I would like on the client is...
/home/username/network/

As I progress I imagine I would eventually like the clients to see...
/home/username/network/photos
/home/username/network/work
/home/username/network/documents
/home/username/network/whatever

...with the actual network source for photos/, work/, documents/, etc. being whatever is a convenient location on the network.

---

### Post by techiebiker on 2014-01-11
...and solved

Decided to post anyway because puzzling over this for days and the act of writing it out to ask for help led me to a solution. Maybe the solution will be helpful to someone else.

Anyway...

On the client
1) sudo mount -t nfs -o proto=tcp,port=2049 **server:/** /home/username/network

is the key.

if server:/ is changed to...

server:/**srv** the client sees the network files in /home/username/network/nfs

and if server:/ is changed to...

server:/**srv/nfs** the client sees the network files in /home/username/network/

which is just what I was trying to achieve.

Probably obvious to those of you familiar with mount but it took me forever to see it!

---

