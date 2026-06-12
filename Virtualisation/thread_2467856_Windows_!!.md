---
title: "Windows !!"
date: 2021-10-09
forum: Virtualisation
---

### Post by PatK100 on 2021-10-09
Hi

Running a Dell 5480 with TPM 2 enabled - 8GB RAM 256 SSD I5 Gen 7 - trying to run Windows 11 Beta under vmware 16 - saying this does not meet minimum specifications - done the encrypted disk and added the TPM support in the Vmware setup - so can anyone help please

Many thanks


Pat

---

### Post by tea for one on 2021-10-09
A Windows 11 ISO intended to be installed on bare metal is apparently not suitable for a VM.

There is a media Creation Tool, which will download the component parts of Windows 11 but removes the requirement for both TPM and UEFI.
A modified ISO is then built.

Here is some info:-

[https://www.tomshardware.com/uk/how-to/install-windows-11-virtual-machine](https://www.tomshardware.com/uk/how-to/install-windows-11-virtual-machine)
[https://gist.github.com/AveYo/c74dc774a8fb81a332b5d65613187b15#file-skip_tpm_check_on_dynamic_update-cmd](https://gist.github.com/AveYo/c74dc774a8fb81a332b5d65613187b15#file-skip_tpm_check_on_dynamic_update-cmd)

---

### Post by tea for one on 2021-10-09
There is also another possible solution here:-
[https://github.com/wimpysworld/quickemu](https://github.com/wimpysworld/quickemu)

---

