---
title: "Lineage 2 - Gracia Second Throne"
date: 2009-04-23
forum: Wine
---

### Post by Coldbird on 2009-04-23
I'm at the loginscreen... but if I press a key or click somewhere it crashes with the following error.
```
2009.4.23 20:55:10
OS : Windows Vista 6.0 (Build: 6001)
CPU : AuthenticAMD Unknown processor @ 1995 MHz with 2047MB RAM
Video : Direct3D HAL (6764)
PosCode : LS1:0:0:0 2/0

General protection fault!

History: TSFImpl::TerminateAllCompositions <- TSFImpl::OnKillFocus <- NTSFIME::ReleaseIME <- NCIMEManager::ReleaseIME <- NCEditBox::OnLostFocus <- NCWnd::ReleaseFocus <- NCVirtualWndMain::ReleaseFocus <- NCVirtualWndMain::HandleMsgLButtonDown <- NCVirtualWndMain::DispatchWndMsg <- NConsoleWnd::DispatchWndMsgX <- NConsoleWnd::MasterConsoleEventProcess <- UEngine::InputEvent <- UWindowsViewport::CauseInputEvent <- UWindowsViewport::UpdateInput <- UViewport::ReadInput <- APlayerController::Tick <- ALineagePlayerController::Tick <- TickAllActors <- ULevel::Tick <- (NetMode=0) <- TickLevel <- UGameEngine::Tick <- UpdateWorld <- MainLoop


```
Wine Shell doesn't give me anything particularly useful... just the usual output. l2.exe is running on Windows Vista config, shaders are deactivated in winecfg.

A little proof screenshot..., I'm running Ubuntu 9.04 btw.
[http://pic.leech.it/i/4b24c/a9c8247bildschirm.png](http://pic.leech.it/i/4b24c/a9c8247bildschirm.png)

---

### Post by cogadh on 2009-04-23
IIRC, Lineage 2 uses GameGuard by default, which doesn't work in Wine. In order to play it, you will probably need to use a private server client, which is a violation of the game's EULA. Don't ask how to do that here, as helping with something potentially illegal like that is against the forum rules. However, it may be possible to run the game using the [Universal Linux Launcher for NCSoft Games]("http://www.lotrolinux.com/ULL/"), so you might give that a shot.

---

