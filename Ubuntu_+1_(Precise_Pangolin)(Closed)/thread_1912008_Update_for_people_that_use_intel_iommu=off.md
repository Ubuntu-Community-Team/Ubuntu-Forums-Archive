---
title: "Update for people that use intel_iommu=off"
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by xyzzyman on 2012-01-19
It appears we won't have to use intel_iommu=off anymore with the 3.2 kernels from Ubuntu. The key line in the change log is:

  * [Config] Disable CONFIG_INTEL_IOMMU_DEFAULT_ON

That's what I've been disabling on my custom compiles so my nVidia card will work without intel_iommu=off. Which is nice as I can install precise now and have it work on first boot!

```
linux (3.2.0-10.17) precise; urgency=low

  [ Andy Whitcroft ]

  * Revert "SAUCE: overlayfs -- fs: limit filesystem stacking depth"
  * Revert "SAUCE: overlayfs -- overlay: overlay filesystem documentation"
  * Revert "SAUCE: overlayfs -- overlayfs: implement show_options"
  * Revert "SAUCE: overlayfs -- overlayfs: add statfs support"
  * Revert "SAUCE: overlayfs -- overlay filesystem"
  * Revert "SAUCE: overlayfs -- vfs: introduce clone_private_mount()"
  * Revert "SAUCE: overlayfs -- vfs: export do_splice_direct() to modules"
  * Revert "SAUCE: overlayfs -- vfs: add i_op->open()"
  * ensure debian/ is not excluded from git by default
  * add new scripting to handle buglinks in rebases
  * ubuntu: overlayfs -- overlayfs: add statfs support
  * ubuntu: overlayfs -- overlayfs: apply device cgroup and security
    permissions to overlay files
    - LP: #915941, #918212
    - CVE-2012-0055

  [ Erez Zadok ]

  * ubuntu: overlayfs -- overlayfs: implement show_options

  [ Leann Ogasawara ]

  * Revert "SAUCE: dmar: disable if ricoh multifunction detected"
  * [Config] Disable CONFIG_INTEL_IOMMU_DEFAULT_ON
    - LP: #907377, #911236
  * [Config] Enable CONFIG_IRQ_REMAP

  [ Miklos Szeredi ]

  * ubuntu: overlayfs -- vfs: pass struct path to __dentry_open()
  * ubuntu: overlayfs -- vfs: add i_op->open()
  * ubuntu: overlayfs -- vfs: export do_splice_direct() to modules
  * ubuntu: overlayfs -- vfs: introduce clone_private_mount()
  * ubuntu: overlayfs -- overlay filesystem
  * ubuntu: overlayfs -- fs: limit filesystem stacking depth

  [ Neil Brown ]

  * ubuntu: overlayfs -- overlay: overlay filesystem documentation

  [ Upstream Kernel Changes ]

  * (pre-stable) x86/PCI: amd: factor out MMCONFIG discovery
    - LP: #647043
  * (pre-stable) PNP: work around Dell 1536/1546 BIOS MMCONFIG bug that
    breaks USB
    - LP: #647043
 -- Leann Ogasawara <leann.ogasawara@canonical.com> Mon, 16 Jan 2012 07:10:08 -0800
```

---

