---
title: "RAID: read performance drop after resync"
date: 2008-09-28
forum: Server Platforms
---

### Post by sminded on 2008-09-28
I did some automated scripted tests with bonnie++ over RAID10 and
encryption, using different encryption cipher modes to evaluate the impact on I/O operations.
The strange thing is that I can see a significant increase in read performance (about 10-15%) when running the tests DURING the raid resync phase directly after the raid creation as appose to running it after the resync, or after I create the array with --assume-clean (which skips initial resync). Without encryption I still see an increase, but not that great.

Have anyone noticed the same behaviour, and how can it be  explained? Any ideas?

Can someone else verify that they get the same result?

My setup:
--------------
OS: Ubuntu Server 8.04
HW: Via Epia C7 1800Mhz (with padlock support, ie hw AES encryption)
Disks: 4x SATAII SAMSUNG Spinpoint 500GB
RAID Setup: Level=10, near=2, far=1, chunksize=64kb, superblock
version= 00.90.03
FS: JFS
Encryption: I'm using dm-crypt with aes-cbc-essiv:sha256, keysize=128,
hash=sha256
Note: Encryption is done on top of the raid array not the other way around

Below is the bonnie++ tests. I made several consecutive tests to get an average.

# bonnie++ during resync with readahead set to 512 (encrypted raid10)
kpax,4G,,,77308,21,34585,17,,,82073,33,384.8,1,,,,,,,,,,,,,
kpax,4G,,,77958,21,34810,17,,,83002,34,394.0,1,,,,,,,,,,,,,
kpax,4G,,,78273,21,34884,17,,,82758,34,389.0,1,,,,,,,,,,,,,

# bonnie++ during resync with readahead set to 65536 (encrypted raid10)
kpax,4G,,,77873,21,34927,18,,,82941,34,367.5,0,,,,,,,,,,,,,
kpax,4G,,,77072,21,34966,18,,,82234,34,357.6,1,,,,,,,,,,,,,
kpax,4G,,,78033,21,34904,18,,,83381,34,372.2,1,,,,,,,,,,,,,

As seen from above, the read throughput from bonnie++ is about  80 MiB /s during resync, regardless of the readahead size on encrypted raid10.

# bonnie++ after resync with readahead set to 512 (encrypted raid10)
kpax,4G,,,81619,22,31528,16,,,70996,28,411.7,1,,,,,,,,,,,,,
kpax,4G,,,81013,22,31341,15,,,68451,28,354.1,1,,,,,,,,,,,,,
kpax,4G,,,81750,22,31291,16,,,69484,28,364.5,0,,,,,,,,,,,,,

# bonnie++ after resync with readahead set to 65536 (encrypted raid10)
kpax,4G,,,81464,22,31348,16,,,69140,28,356.4,1,,,,,,,,,,,,,
kpax,4G,,,81803,22,31039,16,,,67414,27,338.6,1,,,,,,,,,,,,,
kpax,4G,,,81263,22,31361,16,,,70491,28,326.7,0,,,,,,,,,,,,,

The above tests shows that the read throughput drops 15% to about 68 MiB /s  after the resync has finished.

If I run the same set of tests without encryption, I get:

# bonnie++ during resync with readahead set to 512 (normal raid10)
kpax,4G,,,90242,24,58586,20,,,138938,34,320.0,0,,,,,,,,,,,,,
kpax,4G,,,90101,24,53133,19,,,141617,36,414.7,1,,,,,,,,,,,,,
kpax,4G,,,88971,24,53107,19,,,135751,33,437.4,1,,,,,,,,,,,,,
kpax,4G,,,89262,24,53058,19,,,134046,33,411.3,1,,,,,,,,,,,,,

# bonnie++ during resync with readahead set to 65536 (normal raid10)
kpax,4G,,,87487,24,59635,22,,,139171,30,440.3,1,,,,,,,,,,,,,
kpax,4G,,,88879,24,60615,22,,,148133,32,426.5,1,,,,,,,,,,,,,
kpax,4G,,,88836,24,56569,21,,,139867,30,423.0,1,,,,,,,,,,,,,
kpax,4G,,,89166,24,58811,22,,,134982,30,422.2,1,,,,,,,,,,,,,

Now we see that we have alot more juice without the encryption -
pumping about 136 MiB / s during read.

# bonnie++ after resync with readahead set to 512 (normal raid10)
kpax,4G,,,95747,27,45329,17,,,123298,31,546.7,1,,,,,,,,,,,,,
kpax,4G,,,94950,26,45006,16,,,128461,31,476.8,1,,,,,,,,,,,,,
kpax,4G,,,95652,26,45202,16,,,130082,32,442.7,1,,,,,,,,,,,,,
kpax,4G,,,94900,26,44224,16,,,125801,31,455.1,1,,,,,,,,,,,,,

# bonnie++ after resync with readahead set to 65536 (normal raid10)
kpax,4G,,,95475,27,71200,28,,,172074,37,429.2,1,,,,,,,,,,,,,
kpax,4G,,,94724,26,68041,26,,,162545,34,447.5,1,,,,,,,,,,,,,
kpax,4G,,,95133,27,72185,28,,,160979,35,412.8,1,,,,,,,,,,,,,
kpax,4G,,,95090,27,71043,27,,,167199,36,421.7,1,,,,,,,,,,,,,

As seen, even without encryption the read throughput drops after
resync, although not that drastic. The big difference though is that it can be remedied by setting the readahead to 65536

Running plain raid10 with full readahead, shows a whopping (for my setup anyway) 161 MiB /s.

To summarize:
1) There seems to be something fishy going on that makes read
throughput drop a notch after the resync instead of the other way
around.
2) The readahead size does not seem to make any difference on
encrypted raid arrays. This might be as expected.

Request:
Could someone try encryption over raid10 and run bonnie++ tests during and after initial resync to see if we get similar results?
Or just try it without encryption and readahead = 512.

Does anyone have a clue to what this could be?

If anyone have suggestions on preferred raid layout when using
encryption or just plain raid10 please feel free to enlighten me.
Would it be better to try near=2 far=2, or using offset?

---

### Post by fjgaude on 2008-09-28
I would think that any speed tester would have trouble gauging thruputs when an array is resyncing... the readings would be suspect, I would think.

I have no experience in doing what you are doing... the 180MB/sec thruput seems normal, as it's the speed of two of your drives stripped, the raid0 aspect of raid10.

---

### Post by tgalati4 on 2008-09-28
The Via C7 is great for low power (2 to 5 watts), but its performance suffers.  My guess is a caching bottleneck that seems to clear when rsync is running.

---

### Post by fjgaude on 2008-09-28
We are dealing with re-syncing, not rsync, eh?

---

