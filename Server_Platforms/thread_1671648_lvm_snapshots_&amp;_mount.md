---
title: "lvm snapshots &amp; mount"
date: 2011-01-20
forum: Server Platforms
---

### Post by skywarp on 2011-01-20
Hello everyone,

after struggling with this now for couple of months I would like to share this to find out if anybody else is currently experiencing similar problems. 


The Problem:

I am making backups with lvm2 snapshots and GNU tar. So far I think I could track down two symptoms: 

[LIST]

[*]lvcreate fails to create a snapshot volume

[*]snapshot cannot be mounted (mounting it manually works)

[/LIST]

The first one usually fails with error code 5 (error getting status of logical volume). However, the volume is there 
and can be mounted manually.

The latter symptom happens most of the time. Even more confusing: exit code is 0.


Relevant code segement (simplified):

```


sudo lvcreate \

[INDENT]-L 100M \[/INDENT]

[INDENT]-n usr-snapshot \[/INDENT]

[INDENT]-p r \[/INDENT]

[INDENT]-s \[/INDENT]

[INDENT]"/dev/vg0/usr"[/INDENT]

sudo mkdir /mnt/usr

sudo mount -o ro /dev/vg0/usr-snapshot /mnt/usr


```


Orignal code segment:

```


	# Creating logical snapshot volumes. 
	for (( i = 0; i < ${#SNAPSHOT_LV[@]}; i += 2 ))
	do
		$LOGGER "Creating logical volume ${SNAPSHOT_LV[$i]}-snapshot" \
			"with size ${SNAPSHOT_LV[$(($i + 1))]}"
	
		sudo lvcreate \
			-L "${SNAPSHOT_LV[$(($i + 1))]}" \
			-n "${SNAPSHOT_LV[$i]}-snapshot" \
			-p r \
			-s \
			"/dev/vg0/${SNAPSHOT_LV[$i]}"
		RETVAL=$?
		if [ $RETVAL -ne 0 ]; then
			$LOGGER "Creating logical volume ${SNAPSHOT_LV[$i]}-snapshot " \
				"failed. Exit code: $RETVAL."
			
			# Try to restart services at least.
                        services start
			exit 1
		else
			$LOGGER "Logical volume ${SNAPSHOT_LV[$i]}-snapshot " \
				"created."
		fi
		sudo mkdir /mnt/${SNAPSHOT_LV[$i]}
		sudo mount -o ro /dev/vg0/${SNAPSHOT_LV[$i]}-snapshot /mnt/${SNAPSHOT_LV[$i]}
		RETVAL=$?
		if [ $RETVAL -ne 0 ]; then
			$LOGGER "Mounting logical volume ${SNAPSHOT_LV[$i]}-snapshot " \
				"failed. Exit code: $RETVAL."
			
			# Try to restart services at least.
                        services start
			exit 1
		else
			$LOGGER "Successfully mounted logical volume "\
				"${SNAPSHOT_LV[$i]}-snapshot."
		fi
	done
	

```

It is relatively hard to reproduce, as it is not happening every time, however often enough to render 
this backup solution unusable in a production environment.

Anybody having a clue how to track the error down?

Similar problems have been around here and there, too (eg [https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/105936]("https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/105936") ).

Unfortunately, I could not find any substantial help there.


Some background info:

I have six virtual machines running on a Dell PowerEdge 2950 Server System with hardware Raid5 on VmWare vSphere ESXi 4.1. All Systems are fresh Ubuntu 10.04LTS amd64 (Lucid) installs.


Many thanks in advance.

---

### Post by skywarp on 2011-01-20
Dear admins & moderators,

sorry for posting four times. For some reason no response from the server came back upon hitting "submit". 

Therefore, I have marked the redundant posts as Solved though this is not literally the case, but I saw no means to remove these.

---

### Post by psusi on 2011-01-20
"/dev/vg0/usr" should just be vg0/usr

I also use dump instead of tar and don't bother with the read-only flag and don't have any issues.

---

### Post by skywarp on 2011-01-24
Thanks for taking care.

According to man lvcreate /dev/vg0/usr is fine as well. In fact both work.

---

