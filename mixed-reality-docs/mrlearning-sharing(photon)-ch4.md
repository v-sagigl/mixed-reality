---
title: Multi-user capabilities tutorials - 5. Integrating Azure Spatial Anchors into a shared experience
description: Complete this course to learn how to implement multi-user shared experiences within a HoloLens 2 application.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
---

# 4. Integrating Azure Spatial Anchors into a shared experience

In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience. ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.

## Objectives

* Integrate ASA into a shared experience for multi-device alignment
* Learn the fundamentals of how ASA works in the context of a local shared experience

## Preparing the scene

In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab on top of the **TableAnchor** child object in the Hierarchy window to add it to your scene as a child of the TableAnchor object:

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## Configuring the buttons to operate the scene

In this section, you will configure a series of button events that demonstrate the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.

In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:

* To **None (Object)** field, assign the **TableAnchor** object
* From **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:

* To **None (Object)** field, assign the **TableAnchor** object
* From **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function
* To the new **None (Game Object)** field that appears, assign the **TableAnchor** object

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:

* To **None (Object)** field, assign the **TableAnchor** object
* From **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:

* To **None (Object)** field, assign the **TableAnchor** object
* From **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## Connecting the scene to the Azure resource

In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object. Then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mrlearning-sharing(photon)-ch1.md#prerequisites) for this tutorial series:

* In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account
* In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are enabled:

* Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it
* Check the checkbox next to the **Anchor Module Script (Script)** components to enable it
* Check the checkbox next to the **Sharing Module Script (Script)** components to enable it

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## Trying the experience with spatial alignment

> [!NOTE]
> Azure Spatial Anchors can not run in Unity. Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two HoloLens devices.

If you now build and deploy the Unity project to two HoloLens devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID. To test it out, you can follow these steps:

1. On HoloLens device 1: **Start the application** (the Rocket Launcher is instantiated and placed on the table)
2. On HoloLens device 2: **Start the application** (both users see the table with the Rocket Launcher, however, the table does not appear in the same place and the user avatars do not appear where the users are)
3. On HoloLens device 1: Press the **Start Azure Session** button
4. On HoloLens device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).
5. On HoloLens device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)
6. On HoloLens device 2: Press the **Start Azure Session** button
7. On HoloLens device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the HoloLens device 1)

## Congratulations

In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience. This also concludes this tutorial series where you have learned how to set up a Photon account and application, integrate Photon and PUN into a Unity application, configure user avatars and shared objects, and finally align multiple participants using ASA.
