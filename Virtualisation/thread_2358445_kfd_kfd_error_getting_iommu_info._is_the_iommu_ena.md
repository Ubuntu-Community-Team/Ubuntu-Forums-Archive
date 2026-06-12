---
title: "kfd kfd: error getting iommu info. is the iommu enabled?"
date: 2017-04-13
forum: Virtualisation
---

### Post by Robbyx on 2017-04-13
How do I stop the underlying reason for  these error messages? 

```
dmesg | grep error
[    3.686207] kfd kfd: error getting iommu info. is the iommu enabled?
[    3.686333] kfd kfd: device (1002:130f) NOT added due to errors

```
The solution at posting at #9 at [http://bit.ly/2orybCF](http://bit.ly/2orybCF) looked hopeful but in my case this produced no results, so I could not proceed:
```
lspci | grep "SMBus \ | IOMMU"
```

The posting above refers to bios but my board is running under UEFI. 

Robin

---

