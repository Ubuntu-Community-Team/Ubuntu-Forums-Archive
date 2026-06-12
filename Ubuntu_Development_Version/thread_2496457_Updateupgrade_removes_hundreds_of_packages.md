---
title: "Update/upgrade removes hundreds of packages?"
date: 2024-03-28
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2024-03-28
Perhaps stupidly I have been using commands 
[B]sudo apt update
sudo apt full-upgrade[/B] 
on my VMs of Xubuntu Noble most of the time since I started testing this new LTS.

All had been OK until today when the upgrade removed a huge number of packages including several installed manually by me, eg, vlc and audacious plus a huge number of libaudio and python packages making the whole OS unusable and all attempts to add back the packages I wanted that were now gone were impossible due to dependency or broken packages which I could not find or repair.

Let this be a warning perhaps not to use the **full-upgrade** command lightly or you may end with a completely broken system.
Luckily this was just a VM in KVM/QEMU so was of no real consequence to me and very quickly replaced.

However, I thought it worth mentioning and warning users to take care!

---

### Post by jbicha on 2024-03-28
Yes, Ubuntu 24.04 LTS is in the middle of the largest library transition Ubuntu has ever experienced. There is often temporary uninstallability with large transitions. This time is worse and then things got a bit stuck. Hopefully it can be unstuck tomorrow but it is also a holiday weekend for many people.

See also

[https://lists.ubuntu.com/archives/ubuntu-devel/2024-March/042954.html](https://lists.ubuntu.com/archives/ubuntu-devel/2024-March/042954.html)

---

### Post by ajgreeny on 2024-03-29
Thank you for that information; it sounds as ifvi probably will not be the only one who has suffered!

As I say, this was just a testbed virtual install, which is how I test new LTS versions so it was not an important system to me and is already replaced.
I will now just use the upgrade command rather than full-upgrade, just in case.

---

### Post by fthx on 2024-03-29
So I succeeded with Synaptic to update all this mess.
Step by step, carefully. Only accept *t64 switches.
And finally (.................................................) I got them all.

I do not notice sever issues but:
- Plymouth encrypted disk pwd prompt is HUGE
- GS asks me for unlocking my keyring (so classical!)
- I get this odd icon in GS native dash for app grid:
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGQAAABsCAYAAACcsRc5AAAABHNCSVQICAgIfAhkiAAAABl0RVh0U29mdHdhcmUAZ25vbWUtc2NyZWVuc2hvdO8Dvz4AAAAodEVYdENyZWF0aW9uIFRpbWUAdmVuLiAyOSBtYXJzIDIwMjQgMTI6MzM6MTUdLP9xAAALV0lEQVR4nO2dfWwT9R/H37e73rpdN2DrWAcjzG4mrIRoRIc1BKISpGSKkWwNIvJg1AVUQiQhTGL4Y0QIRvAfzSQylghREyMyY3AuGDYYTBB5ZjDGtsBW3HO3bq1d1/MPsuY3227f6z304Pd9/dXdfZ/W1 6 93343Bir1SqCohsS4t0AynioEJ1BhegMKkRncHl5efFuw0NBMBhEIBCA3H1 vF8PAwRkZGFK HmTVrFn3KIoBlWRgMBiQmJiI5ORkmkwmBQAButxsejweiqMzXSIXECMMwEAQB6enp4DgO3d3dGB4ell0up0Db/i8RRREejwcejwcmkwmZmZnwer3o7u6WdbXQTl0BPB4PWlpaAADZ2dlgWTbmsqgQhQgGg jo6IDb7cbMmTNjlkKFKExPTw/cbjdmzJgBhmEk56dCVKC7uxs nw8ZGRmS81IhKnH//n0kJSUhOTlZUj4qRCWCwSDu378Ps9ks6dZFhaiIx NBIBCAIAjEeagQlenp6cHUqVOJ01MhKjM0NASO42AwGIjSUyEqI4oihoaGkJSURJSeCtEAKkRn P1 8DxPlJYK0YCRkRFwHNk8LhWiAaOjo0hIIPuqqRANEEWReHBIhegMKkRnUCE6gwrRGVSIzqBCdAYVojOoEJ1BhegMKkRn6H7nIsdxCAQCEc9ZrVY4HA7k5eXBaDTC5XLh1KlTOHnyJEZHRzVuqTLoRojZbEZBQQGeeOIJ2Gw2ZGVlYdq0aTAajRBFEevWrcP58 cBAImJidi fTtWrlwZNmnndDpx /ZtbNu2DY2NjfH4VWQRVyE8z8PhcODll19GQUFB1N1 P/74Y0gGx3H48ssvsWDBgqjl5uXl4ZtvvsHatWtx7do1VdquFnERwnEcli9fjk2bNiE7O3vS9JWVlaHPJSUlE8oYIykpCfv370dhYSHecfWe3VEs079blz5 KHH37AJ598QiSjpaUFt2/fBgAIgoB169YR1zVjxgysWLEi1qbGBc2EMAyDjRs34siRI5AStXXp0qXQZ7vdTrw2PcYLL7wgKX280eSWZTAYUFZWhsLCwknTer1eNDY24saNG jr68PZs2dD52bNmiW57ljyxBPVhfA8jy AJ2uz1qmmAwiJqaGhw7dgz19fVR7/nBYFBy/bHkiSeqCmEYBrt27ZpQRk1NDT777DO0tbVNWl5ra6vkNsSSJ56oKuS9997D8uXLI54bGBjARx99hBMnThCX19DQgMHBQaSkpBDn e2334jT6gHVOvUnn3wSb7/9dsRzra2tKC4uliQDAHw H8rLy4nTNzU14Zdffgn9TLqdM56oIiQxMRFlZWURB3qtra1Yv3497t69G1PZlZWVqK6unjRdb28vtmzZEpp2sdvteOutt2KqU0tUC4s2GAwwm82wWq14/vnn8corr0AURRQXFxP1FxPBsixKSkqwYcMGGI3GsPMNDQ3YsWMHOjo6AABGoxHff/89LBYLli1bht7eXln1x0J fn5oPDURmsWpT5s2DdnZ2bhy5YpiZZrNZixZsgS5ubkQBAHt7e2oq6vD5cuXQ2lYlsWePXvgcDgAAEeOHMGuXbsUawMpcRdiNBrh8/nUKJoYQRBQVlaGpUuXho55vV4sWrRIkSB/KZAKUawP4TgORUVFOHz4MP766y/8 eefaGhowOeff45nnnlGqWoksXbt2nEygAdzXC GJc2kMCO2XKlJ1yC8nMzMTXX3 N4uJiWCyWUGfO8zysViteffVVmM1mnD59WtOB2r1797B69eqwKXqj0Yiff/5Zs3YAQEZGBlHfJfsKEQQBX331FebOnTthOqfTidLSUrnVScLlcuHkyZNhx5999lni8ACtkS2kpKSEeLLQ6XQSTZ0rSW1tbdgxjuOQm5uraTtIkSWE53k4nU5JeV5//XU5VUrmwoULEY/bbDZN20GKLCE2m01SyC8Aza QO3fuYGhoKOz4I3mFmM1myXlSUlIiDubUQhRF9PX1hR2Xuq6iFbKEeDweyXn8fr/mS6qR2qnlH4UUZAm5ceNG1C060bh69apir8Mjxe/3hx1LTEzUtA2kyBLidrvx /S8pz9OhROVXGxPTp08OO9ff3a94OEmQ/9u7bty9ipxmJy5cv46effpJbpSQ4jov4mqSxiUe9IVtIW1sbNm/ePKmUmzdvYvPmzZJvcXJ57LHHIi4DuFwuTdtBiiJzWWfOnEFRURGqq6vDvvDBwUEcOHAAb7zxBjo7O5WoThKLFy OeLypqUnjlpCh2BJuW1sbtmzZgtTUVOTn5yMlJQVdXV24du2a5lfF/xJpIrGrq vRFzLGwMAAGhoalC42JubMmYN58 aFHa rq9P8SY8U1bcBpaamYuHChQgGgzh /Lja1Y3j/fffjxiwL/XJUEsUF5KVlYWKigr4fD6YTCZkZWUBeDA4O3fuHHp6epSuMiImkyniOkxbW1vEGWC9oLgQl8uFK1euhG3/MZlMKCsrw8aNG2XfLpKTk1FYWAi73Y7p06djcHAQjY2NqKqqQnNzM4AHfwAbNmzAoUOHxk2TVFZW6jp2RJEFqv/S0tKCoqKisIWh2bNnY3R0NBRaEAuLFy/GwYMH4XA4kJubC4vFgtmzZ2P /PlwOp1IS0vD2bNnEQwG0dnZCZfLhSVLlgAA/v77b3z88cdxecggXaBSRUhvby SkpLw1FNPhZ0rKChAX18frl69KrncpUuXYv/ /VFnmBmGwbx58zBnzhwcP34coiji1q1beO6555CVlYXS0tK4PV3FVQgAXLx4ES 99FLYCyAZhsGiRYtgMBhw7tw54tuX2WzGwYMHieagcnJy4Ha7Q7tPPB4P/H4/Dhw4IP0XUQjNlnCj4fP58MEHH0Qdwb/zzjuoqKggihEBgDfffFPSS4nffffd0Ai9trYWu3fvJs4bT1SND2lubsbWrVuj3rOffvppVFVVobS0NPQ0Fo1oI 5opKWlhcYgPp8PbrdbUv54oXrATm1tLT788MOIU DAg2Xg1atXo7q6GuXl5Vi1ahWsVmvYK/FIryS5eeKNJhFUNTU12LRpEwYHB6M3JCEBCxcuxI4dO1BVVYXz58 P 0JjeTJS439EqY1mIW319fV47bXXxm3znAiDwYCZM2eGfh4bX0hh7J sPExoGvTZ0dGBNWvWYO/evRNeLWPMnz8/9PnXX3 VVNedO3dw69YtyW2MN5pH4QYCARw6dAgOhwMVFRUTdrbLli0LzUV99913ktYw9u3bJ7ut8UC1cchk Hw 1NfX4/Dhw6HwhMzMzHE7CtPS0tDU1ITm5mYEAgH88ccfcDgck45FysvL8e2336rafqmQjkN09W/zOI6DzWbD448/jpycHEydOhVerxe7d 8O7QnOycnBzp07I04c9vb24tNPP9V8mZiEuIcjqI3NZoPdbofFYsHAwAAaGxtRV1cX9xCIaJAK0c3LZ6Ry/fp1XL9 Pd7NUBz6viydQYXoDCpEZ1AhOoMK0RlUiM6gQnQGFaIzqBANYBiGeO8AFaIBLMsSx dTIRpgMBiIVzypEA3geT7qnoL/QoVogCAI8Hq9RGmpEA2gQnSEyWRCIBAg3gFDhaiM2WyWtEmPClERk8kElmUlvWCBClEJlmVhsVjQ1dUlKR6GClEJi8WC4eFh4s58DCpEBTIyMsDzPLq7uyXnpUIUJj09Hampqejo6IgpdO h3XWiN8b6DJ7n0d7eHvO7JakQBTCZTKE o729XVZQKxUig5SUFKSnp4NlWXR2dkruwCNBhRDAMAwSEhLA8zx4nocgCBAEAYFAAP39/RgaGlLszRBcfn6 IgU9yoiiCFEUMTIyAr/fD6/Xi/7 flUCghir1fpQ7u19VPkXdnf8H9BjCWwAAAAASUVORK5CYII=[/IMG]
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGQAAABsCAYAAACcsRc5AAAABHNCSVQICAgIfAhkiAAAABl0RVh0U29mdHdhcmUAZ25vbWUtc2NyZWVuc2hvdO8Dvz4AAAAodEVYdENyZWF0aW9uIFRpbWUAdmVuLiAyOSBtYXJzIDIwMjQgMTI6MzM6MTUdLP9xAAALV0lEQVR4nO2dfWwT9R/H37e73rpdN2DrWAcjzG4mrIRoRIc1BKISpGSKkWwNIvJg1AVUQiQhTGL4Y0QIRvAfzSQylghREyMyY3AuGDYYTBB5ZjDGtsBW3HO3bq1d1/MPsuY3227f6z304Pd9/dXdfZ/W1 6 93343Bir1SqCohsS4t0AynioEJ1BhegMKkRncHl5efFuw0NBMBhEIBCA3H1 vF8PAwRkZGFK HmTVrFn3KIoBlWRgMBiQmJiI5ORkmkwmBQAButxsejweiqMzXSIXECMMwEAQB6enp4DgO3d3dGB4ell0up0Db/i8RRREejwcejwcmkwmZmZnwer3o7u6WdbXQTl0BPB4PWlpaAADZ2dlgWTbmsqgQhQgGg jo6IDb7cbMmTNjlkKFKExPTw/cbjdmzJgBhmEk56dCVKC7uxs nw8ZGRmS81IhKnH//n0kJSUhOTlZUj4qRCWCwSDu378Ps9ks6dZFhaiIx NBIBCAIAjEeagQlenp6cHUqVOJ01MhKjM0NASO42AwGIjSUyEqI4oihoaGkJSURJSeCtEAKkRn P1 8DxPlJYK0YCRkRFwHNk8LhWiAaOjo0hIIPuqqRANEEWReHBIhegMKkRnUCE6gwrRGVSIzqBCdAYVojOoEJ1BhegMKkRn6H7nIsdxCAQCEc9ZrVY4HA7k5eXBaDTC5XLh1KlTOHnyJEZHRzVuqTLoRojZbEZBQQGeeOIJ2Gw2ZGVlYdq0aTAajRBFEevWrcP58 cBAImJidi fTtWrlwZNmnndDpx /ZtbNu2DY2NjfH4VWQRVyE8z8PhcODll19GQUFB1N1 P/74Y0gGx3H48ssvsWDBgqjl5uXl4ZtvvsHatWtx7do1VdquFnERwnEcli9fjk2bNiE7O3vS9JWVlaHPJSUlE8oYIykpCfv370dhYSHecfWe3VEs079blz5 KHH37AJ598QiSjpaUFt2/fBgAIgoB169YR1zVjxgysWLEi1qbGBc2EMAyDjRs34siRI5AStXXp0qXQZ7vdTrw2PcYLL7wgKX280eSWZTAYUFZWhsLCwknTer1eNDY24saNG jr68PZs2dD52bNmiW57ljyxBPVhfA8jy AJ2uz1qmmAwiJqaGhw7dgz19fVR7/nBYFBy/bHkiSeqCmEYBrt27ZpQRk1NDT777DO0tbVNWl5ra6vkNsSSJ56oKuS9997D8uXLI54bGBjARx99hBMnThCX19DQgMHBQaSkpBDn e2334jT6gHVOvUnn3wSb7/9dsRzra2tKC4uliQDAHw H8rLy4nTNzU14Zdffgn9TLqdM56oIiQxMRFlZWURB3qtra1Yv3497t69G1PZlZWVqK6unjRdb28vtmzZEpp2sdvteOutt2KqU0tUC4s2GAwwm82wWq14/vnn8corr0AURRQXFxP1FxPBsixKSkqwYcMGGI3GsPMNDQ3YsWMHOjo6AABGoxHff/89LBYLli1bht7eXln1x0J fn5oPDURmsWpT5s2DdnZ2bhy5YpiZZrNZixZsgS5ubkQBAHt7e2oq6vD5cuXQ2lYlsWePXvgcDgAAEeOHMGuXbsUawMpcRdiNBrh8/nUKJoYQRBQVlaGpUuXho55vV4sWrRIkSB/KZAKUawP4TgORUVFOHz4MP766y/8 eefaGhowOeff45nnnlGqWoksXbt2nEygAdzXC GJc2kMCO2XKlJ1yC8nMzMTXX3 N4uJiWCyWUGfO8zysViteffVVmM1mnD59WtOB2r1797B69eqwKXqj0Yiff/5Zs3YAQEZGBlHfJfsKEQQBX331FebOnTthOqfTidLSUrnVScLlcuHkyZNhx5999lni8ACtkS2kpKSEeLLQ6XQSTZ0rSW1tbdgxjuOQm5uraTtIkSWE53k4nU5JeV5//XU5VUrmwoULEY/bbDZN20GKLCE2m01SyC8Aza QO3fuYGhoKOz4I3mFmM1myXlSUlIiDubUQhRF9PX1hR2Xuq6iFbKEeDweyXn8fr/mS6qR2qnlH4UUZAm5ceNG1C060bh69apir8Mjxe/3hx1LTEzUtA2kyBLidrvx /S8pz9OhROVXGxPTp08OO9ff3a94OEmQ/9u7bty9ipxmJy5cv46effpJbpSQ4jov4mqSxiUe9IVtIW1sbNm/ePKmUmzdvYvPmzZJvcXJ57LHHIi4DuFwuTdtBiiJzWWfOnEFRURGqq6vDvvDBwUEcOHAAb7zxBjo7O5WoThKLFy OeLypqUnjlpCh2BJuW1sbtmzZgtTUVOTn5yMlJQVdXV24du2a5lfF/xJpIrGrq vRFzLGwMAAGhoalC42JubMmYN58 aFHa rq9P8SY8U1bcBpaamYuHChQgGgzh /Lja1Y3j/fffjxiwL/XJUEsUF5KVlYWKigr4fD6YTCZkZWUBeDA4O3fuHHp6epSuMiImkyniOkxbW1vEGWC9oLgQl8uFK1euhG3/MZlMKCsrw8aNG2XfLpKTk1FYWAi73Y7p06djcHAQjY2NqKqqQnNzM4AHfwAbNmzAoUOHxk2TVFZW6jp2RJEFqv/S0tKCoqKisIWh2bNnY3R0NBRaEAuLFy/GwYMH4XA4kJubC4vFgtmzZ2P /PlwOp1IS0vD2bNnEQwG0dnZCZfLhSVLlgAA/v77b3z88cdxecggXaBSRUhvby SkpLw1FNPhZ0rKChAX18frl69KrncpUuXYv/ /VFnmBmGwbx58zBnzhwcP34coiji1q1beO6555CVlYXS0tK4PV3FVQgAXLx4ES 99FLYCyAZhsGiRYtgMBhw7tw54tuX2WzGwYMHieagcnJy4Ha7Q7tPPB4P/H4/Dhw4IP0XUQjNlnCj4fP58MEHH0Qdwb/zzjuoqKggihEBgDfffFPSS4nffffd0Ai9trYWu3fvJs4bT1SND2lubsbWrVuj3rOffvppVFVVobS0NPQ0Fo1oI 5opKWlhcYgPp8PbrdbUv54oXrATm1tLT788MOIU DAg2Xg1atXo7q6GuXl5Vi1ahWsVmvYK/FIryS5eeKNJhFUNTU12LRpEwYHB6M3JCEBCxcuxI4dO1BVVYXz58 P 0JjeTJS439EqY1mIW319fV47bXXxm3znAiDwYCZM2eGfh4bX0hh7J sPExoGvTZ0dGBNWvWYO/evRNeLWPMnz8/9PnXX3 VVNedO3dw69YtyW2MN5pH4QYCARw6dAgOhwMVFRUTdrbLli0LzUV99913ktYw9u3bJ7ut8UC1cchk Hw 1NfX4/Dhw6HwhMzMzHE7CtPS0tDU1ITm5mYEAgH88ccfcDgck45FysvL8e2336rafqmQjkN09W/zOI6DzWbD448/jpycHEydOhVerxe7d 8O7QnOycnBzp07I04c9vb24tNPP9V8mZiEuIcjqI3NZoPdbofFYsHAwAAaGxtRV1cX9xCIaJAK0c3LZ6Ry/fp1XL9 Pd7NUBz6viydQYXoDCpEZ1AhOoMK0RlUiM6gQnQGFaIzqBANYBiGeO8AFaIBLMsSx dTIRpgMBiIVzypEA3geT7qnoL/QoVogCAI8Hq9RGmpEA2gQnSEyWRCIBAg3gFDhaiM2WyWtEmPClERk8kElmUlvWCBClEJlmVhsVjQ1dUlKR6GClEJi8WC4eFh4s58DCpEBTIyMsDzPLq7uyXnpUIUJj09Hampqejo6IgpdO h3XWiN8b6DJ7n0d7eHvO7JakQBTCZTKE o729XVZQKxUig5SUFKSnp4NlWXR2dkruwCNBhRDAMAwSEhLA8zx4nocgCBAEAYFAAP39/RgaGlLszRBcfn6 IgU9yoiiCFEUMTIyAr/fD6/Xi/7 flUCghir1fpQ7u19VPkXdnf8H9BjCWwAAAAASUVORK5CYII=[/IMG]
(well for whatever reason the icon does not display here, but that's b/w Ubuntu circle icon)

---

### Post by ajgreeny on 2024-03-29
I have decided to leave this alone at the moment!
The one hard-metal install of Xubuntu I have which I installed a long time ago was messed up in those upgrades yesterday and I can't get back I need so I'm not going to keep trying just yet.
Even the Libreoffice applications, eg Writer and Calc fail to open and don't even show separately in the Whisker menu at the moment; I tried reinstalling all the Libreoffice packages but still no good.
I will now wait until after Easter and then try again with a new ISO next week in the hope that all will be better.

PS:
@ fthx
what do you mean by "Only accept *t64 switches."

---

### Post by Doug S on 2024-03-29
I got caught up in this update mess yesterday. I was initially excited when I got an email from [a bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2051342") that kernel 6.8.0-20-generic had been released. My 24.04 desktop VM now has [no network]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/2059651") and the workarounds seem to require a network. I am a server person, and only use the desktop do do work on ubuntu-docs for publishing on help.ubuntu.com. My 24.04 Ubuntu server seems to have survived the update. The 6.8.0-20-generic kernel didn't show up until today (I'll start another thread about that).

EDIT: after a workaround post to the network-manager gets deleted bug report, I was able to get the network working again on my 24.04 desktop VM. Tons more updates, but still 4 packages being held back, due to dependency issues with non-existent packages. I'll just wait before trying again.

---

### Post by jbicha on 2024-03-29
@fthx Could you report those bugs?

Yes, most of the transitions are done now. But there are still a few uninstallable packages.

---

### Post by Smask on 2024-03-29
> **jbicha said:**
> Yes, most of the transitions are done now. But there are still a few uninstallable packages.

Massaged Synaptic to update all but **gnome-remote-desktop **and **yaru-theme-gnome-shell** and then rebooted.

Success!!!

First full reboot since Mar 4, when I couldn't boot further than graphics mode and mouse pointer worked for about 4-5 seconds (failed to start the greeter?) and nothing more, no ability to switch to virtual terminals or so. The only way to access the computer was by by booting via the recovery mode.

---

### Post by jbicha on 2024-03-29
Yes, gnome-shell & mutter need to migrate to clear up those mentioned uninstallable packages.

---

### Post by #&amp;thj^% on 2024-03-29
On my end all is good:
```
Summary                                                                                 
=========================================================================================
 Upgrade      126 Packages                                                               
 Kept Back   1020 Packages                                                               
 Auto-Remove    9 Packages                                                               
                                                                                         
 Total download size  134.5 MB   
 Disk space to free    24.5 MB   
```

jbicha look away quick, your not going to want to see this.....LOL 5532 pkgs from proposed [https://paste.ubuntu.com/p/BjTbY8RqST/](https://paste.ubuntu.com/p/BjTbY8RqST/)

---

### Post by fthx on 2024-03-29
@Jeremy: already reported except keyring that I have to investigate first.

---

### Post by ajgreeny on 2024-03-29
There's still several packages that are impossible to install on my system from yesterday such as vlc and audacity, but probably many more as well as I tried only those two after upgrading everything this afternoon, 29 March.

---

### Post by Doug S on 2024-03-29
> **ajgreeny said:**
> There's still several packages that are impossible to install on my system from yesterday such as vlc and audacity, but probably many more as well as I tried only those two after upgrading everything this afternoon, 29 March.

Same here.

---

### Post by Irihapeti on 2024-03-30
Methinks I might leave a few systems strictly alone until this is all sorted out, hopefully in a day or three.

---

### Post by ajgreeny on 2024-03-30
> **Irihapeti said:**
> Methinks I might leave a few systems strictly alone until this is all sorted out, hopefully in a day or three.
That's what I said a couple of days ago but my curiosity, and the ease of installing in KVM/QEMU seems to get the better of me, leading to me updating my most recent ISO using zsync and then installing that in the hope - - -.
Ah well, only 3 weeks to go unless this turns into another 6.04 which became 6.06. And very good it was too!

Oh gosh! I'm obviously getting old!

---

### Post by fthx on 2024-03-30
What's the point now with all these packages in noble-updates?
t64 is cancelled? xz-related?

What do we have to do, now?

---

### Post by ajgreeny on 2024-03-30
I suspect we just have to wait and then get a new ISO to try another installation.

Incidentally, following a normal update last night, 29 March, of my installation installed using a 28 March ISO, I am now back to the problem of Xubuntu not moving to the GUI desktop but staying in command line unless I login to the tty1 that is showing and use **startx** command.

---

### Post by fthx on 2024-03-30
so that's xz-related  [https://discourse.ubuntu.com/t/whats-happening-in-noble-repositories/43729/7](https://discourse.ubuntu.com/t/whats-happening-in-noble-repositories/43729/7)

---

### Post by MAFoElffen on 2024-03-31
The only thing I noticed happening wrong was a network "bond" config broke on one of my test servers... 

Dang. I feel very lucky.

---

### Post by Irihapeti on 2024-04-01
I wonder if the err... actor decided to try to push the bad version in under the cover of the big library update. At the moment, nothing would surprise me.

I'm not aware of anything wrong with any of my current Noble installs, but once the dust has settled, I think I'll blow them all away and start again, as suggested in the thread above. Meantime, if I really need to use any of the devices in question, there is always a stable release available.

I think we have all been extraordinarily lucky. 8-[

---

### Post by ajgreeny on 2024-04-02
> **rikazkhan7 said:**
> It sounds like you've encountered issues with using the sudo apt full-upgrade command on your Xubuntu Noble VMs. This command is intended to upgrade all installed packages to their latest versions, including any dependencies, which can sometimes lead to unexpected changes or removals of packages.
In your case, it seems that the full-upgrade command resulted in the removal of essential packages, including ones you had manually installed like VLC and Audacious, as well as various library and Python packages. This left your operating system in an unusable state, with broken dependencies preventing you from reinstalling the removed packages.
It's essential to exercise caution when using the full-upgrade command, especially on production systems or VMs where data loss or downtime can have consequences. Instead, consider using the sudo apt upgrade command, which only upgrades packages that have new versions available, without removing any existing packages unless absolutely necessary.
Additionally, it's a good practice to regularly backup your system or VM before performing any significant upgrades or changes, so you can quickly restore it to a working state if something goes wrong.
Absolutely correct!

The reason I use a VM, not a hard metal installation that is used for business or important personal use, is simply to test such things; if anything terrible goes wrong I just delete the VM and start again with a new ISO file.

There is no way I would ever run a dev version as my main system but VMs are a great way to check everything.
At the moment, of course, there are no new updated ISOs to test but as soon as a new one appears I shall download and create a new VM.

---

### Post by IanW on 2024-04-03
The latest news is that the beta release of Noble has been pushed back a week to April 11th.
Source - [https://discourse.ubuntu.com/t/noble-numbat-beta-delayed-xz-liblzma-security-update/43827](https://discourse.ubuntu.com/t/noble-numbat-beta-delayed-xz-liblzma-security-update/43827)

---

