---
title: "creating new filesystem"
date: 2018-04-21
forum: Ubuntu Application Development
---

### Post by nd18 on 2018-04-21
Hi, 
I'm trying to create an simple filesystem and I have doubts to manage the structures.
The requirements of the system are: 
(1) Files: max files are 40, max size file 1048576 bytes, name file 32 bytes and checksum redundancy with crc16/32.
(2) Device: min size 50Kib / max size 10MiB
(3) Size block to manage the system 2048 bytes

I think the useful structures to manage the superblock and inode are:
  char name [32]; //name
  uint16_t bytesUsed; //bytes used to the file
  uint8_t directBlock; 
  uint8_t opened; //open/close file
  uint16_t pointer; //pointer file
  uint16_t checksum; //integrity crc

And superblock
  long diskSize; //size disk
  uint32_t INodoMap; //inodes map
  struct inode nodes [MAX_FILES]; //nodes
  uint16_t checksum; /integrity with crc

I don't know if I need to modify or add anything but I'm not sure because the file could size more than one block.

Please, anybody help me?
Kind regards.

---

