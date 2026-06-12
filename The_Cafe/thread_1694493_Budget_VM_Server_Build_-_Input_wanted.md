---
title: "Budget VM Server Build - Input wanted"
date: 2011-02-24
forum: The Cafe
---

### Post by 98cwitr on 2011-02-24
Your thoughts plz, budget is around $1500, but the lower the better. Ubuntu main OS.

Uses:
Torrents
Media Server (java)
VirtualBox

> 	
Antec Atlas 550 Black Server Case
Model #:Atlas 550
Item #:N82E16811129020
Return Policy:Standard Return Policy
In Stock
$169.99	 	$169.99
	
ASUS KCMA-D8 Dual Socket C32 AMD SR5670 ATX Dual AMD Opteron 4100 Series 4/6 Core Processor Server Motherboard
Model #:KCMA-D8
Item #:N82E16813131670
Return Policy:Standard Return Policy
In Stock
Mail in Rebate Card
$289.99	 	$289.99
	
AMD Opteron 4130 Lisbon 2.6GHz Socket C32 115W Quad-Core Server Processor OS4130WLU4DGNWOF
Model #:OS4130WLU4DGNWOF
Item #:N82E16819105276
Return Policy:CPU Replacement Only Return Policy
In Stock
$134.99	 	$269.98
	
Kingston 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 ECC Unbuffered Server Memory Model KVR1333D3E9SK2/4G
Model #:KVR1333D3E9SK2/4G
Item #:N82E16820139040
Return Policy:Memory Standard Return Policy
In Stock
$50.99	 	$203.96
	
Western Digital Caviar Green WD20EADS 2TB SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive
Model #:WD20EADS
Item #:N82E16822136344
Return Policy:Standard Return Policy
In Stock
$99.99	 	$299.97
	
ZALMAN CNPS8000A 92mm 2 Ball CPU Cooling Fan/Heatsink
Model #:CNPS8000A
Item #:N82E16835118062
Return Policy:Standard Return Policy
In Stock
$41.99	-$14.00 Instant	$55.98
Subtotal:	$1,289.87


---

### Post by CharlesA on 2011-02-24
Looks good. I think it's a bit overkill for a "budget" build, but it also depends on what you are going to be using it for.

Torrents don't really take that much CPU power, and depending on how many VMs you are going to have running at the same time, you might be able to get away with just a quad core.

---

### Post by cprofitt on 2011-02-24
I assume from the total that you are installing 16GB of ram... I might push that to 32GB if you can.

---

### Post by 98cwitr on 2011-02-24
I wont be running over 10 VMs I don't think...I was thinking about putting a SSD in for the primary...but I'm trying to go cheap and still have 2 CPUs.

VMs to consider:
1. Fedora - bash programming tester, wireshark, Apache, backtrack
2. Solaris 10 - Have need to learn solaris at some point in my life :D
3. Windows 7 - Test client, powershell scripting
4. Windows Server 2008 - AD, DNS, DFS, DHCP, SQL, Exchange (all for work testing)
5. Windows XP - Test client
6. Windows Server 2003 - AD replication testing, 2nd DNS
7. Windows Server 2003 - QC/Test
8. Windows Server 2008 - outside IIS, OWA 

16GB should be plenty :)

---

### Post by CharlesA on 2011-02-24
Sounds nice. I've got 6GB of RAM in my VM host, running around 4 to 6 VMs at a time (most with 512MB of RAM)

---

### Post by Shining Arcanine on 2011-02-24
> **cprofitt said:**
> I assume from the total that you are installing 16GB of ram... I might push that to 32GB if you can.

When I last checked a week ago, 4GB modules cost roughly 2.5 times more than 2GB modules at Newegg.com. I doubt that most people would want to use them until their cost per GB reaches parity with the 2GB modules.

---

### Post by kevin11951 on 2011-02-25
I would recommend changing from Ubuntu to Proxmox VE:

[http://www.youtube.com/watch?v=Ly1BLt0s0zI&feature=player_embedded](http://www.youtube.com/watch?v=Ly1BLt0s0zI&feature=player_embedded)

Forgot to post the actual link: [http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

---

### Post by 98cwitr on 2011-02-25
does that OS support all VHD types?

Also, would you folks be kind enough to check out the mobo and tell me if those cpu fans are going to fit?

---

### Post by CharlesA on 2011-02-25
> **98cwitr said:**
> 
Also, would you folks be kind enough to check out the mobo and tell me if those cpu fans are going to fit?

The CPUs use socket C32. Newegg doesn't sell any heatsinks that fit those sockets. They carry some for a G34 socket, and a F socket.

[These guys]("http://www.dynatron-corp.com/en/product_list.aspx?cv=1-3-294") carry heatsinks for C 32 sockets.

---

### Post by 98cwitr on 2011-02-25
I was informed that the AM3 heatsinks fit the C32s on the ASUS boards:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819105276](http://www.newegg.com/Product/Product.aspx?Item=N82E16819105276)

---

### Post by CharlesA on 2011-02-25
If that's the case, then it should fit, as there is plenty of space between the sockets.

---

### Post by kevin11951 on 2011-02-25
> **98cwitr said:**
> does that OS support all VHD types?

Also, would you folks be kind enough to check out the mobo and tell me if those cpu fans are going to fit?

It supports VMDK (virtualbox/vmware) among others...

---

