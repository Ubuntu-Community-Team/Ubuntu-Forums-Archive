---
title: "KVM/virsh - cannot parse pool.xml"
date: 2010-10-16
forum: Server Platforms
---

### Post by fistikuffs on 2010-10-16
I've got KVM running on on server 10.04 and I'm trying to add a second hard disk as a store for my images is /var/libvirt/images is on a small partiton.
I've dumped pool.xml and had a stab at editing to include the second disk but I'm not sure of the proper syntax and i keep getting "*error: XML description for failed to parse xml document is not well formed or invalid*"

Here's a copy of my edited pool.xml. I got the uuid with blkid and the capacity values from multiplying df output by 1024


```
<pool type='dir'>
  <name>default</name>
  <uuid>3baf6efa-09c7-dd94-d184-7a4ac4f86ffd</uuid>
  <capacity>21017522176</capacity>
  <allocation>1197379584</allocation>
  <available>19820142592</available>
  <source>
  </source>
  <target>
    <path>/var/lib/libvirt/images</path>
    <permissions>
      <mode>0700</mode>
      <owner>0</owner>
      <group>0</group>
    </permissions>
  </target>
<pool type='dir'>
  <name>vmstore</name>
  <uuid>8f04f8dd-c78d-4595-844f-542b2fb0e3ca</uuid>
  <capacity>492257886208</capacity>
  <allocation>467045011456</allocation>
  <available>467045011456</available>
  <source>
  </source>
  <target>
    <path>/dev/sdb5</path>
    <permissions>
      <mode>0700</mode>
      <owner>0</owner>
      <group>0</group>
    </permissions>
  </target>
</pool>
```

I only tried /dev/sdb5 out of desperation. I haved tried the disks mount point too.

Does anyone the proper way to add my second this to the pool?

---

