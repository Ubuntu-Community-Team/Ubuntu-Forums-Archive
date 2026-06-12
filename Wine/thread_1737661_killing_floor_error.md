---
title: "killing floor error"
date: 2011-04-23
forum: Wine
---

### Post by ELD on 2011-04-23
Hi all trying to get killing floor to run and it crashes out with this:

> 
ReadFile beyond EOF 0+4/0

History: ULinkerLoad::Serialize <- FUnrealfileSummary<< <- LoadSummary <- ULinkerLoad::ULinkerLoad <- UObject::GetPackageLinker <- ULinkerLoad::VerifyImport <- ValidateImports <- ULinkerLoad::Verify <- ULinkerLoad::ULinkerLoad <- UObject::GetPackageLinker <- UObject::StaticLoadObject <- (Engine.LevelSummary KF-Departed.LevelSummary NULL) <- UCacheManager::ExportCacheMaps <- NewMaps <- UCacheManager::SaveNewPackages <- UCacheManager::InitCache <- UCacheManager::execInitCache <- (KFGUIController Package.KFGUIController @ Function XInterface.GUIController.InitializeController : 01BB) <- UObject::execClassContext <- (KFGUIController Package.KFGUIController @ Function XInterface.GUIController.InitializeController : 01BB) <- UObject::ProcessEvent <- (KFGUIController Package.KFGUIController, Function KFGUI.KFGUIController.InitializeController) <- UGameEngine::Init <- InitEngine <- FMallocWindows::Free <- FMallocWindows::Free




---

### Post by cogadh on 2011-04-23
Error messages produced by the application itself are mostly useless in Wine, we need Wine's error output, which you can only get by running the game from the terminal.

That being said, have you followed the how-to found here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=16616&iTestingId=40524](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16616&iTestingId=40524)

---

