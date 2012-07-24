# specs2-plugin-demo #

This is a temporal repository for storing the build of the Specs2 extension of the ScalaTest plugin for the ScalaIDE.

For the list of features, please check out the [project site][projectSite].

## Required Build Configuration ##
**Please note this version is only a demo version.**

The required configuration is:

* JRE 1.5+. It is enough to use it only for running Eclipse, just set it with the `-vm` switch within the *eclipse.ini* file [as described here][eclipseIni])
* My master Scala IDE fork (2.1.x) with stable Scala (2.9.2). Some features won't work with the the original one (e.g., the new wizards) (+)
* My ScalaTest plugin fork. Note that it is not the latest one. (+)

(+) Steps to install these plugins are detailed below.

## Steps to install the plugin ##

1. [Download Eclipse Indigo][IndigoDownload] (3.7.2). The *"Classic"* version is perfect.
   Note that there is no experience using this plugin with Juno at the moment. Would be great to hear any comments though! ;-)
1. Clone the repository:
   
		$ git clone https://github.com/rlegendi/specs2-plugin-demo.git
   
1. In Eclipse, click *Help* --> *Install New Software*
   1. Click *Add*
   1. Write *scala-ide* into the *Name* field
   1. Click *Local*
   1. Browse the *scala-ide/site* directory of the cloned project
   1. Install the plugin (+) (++)
   1. Repeat these steps for the *scalatest* and *specs2* plugins in this order.
1. Done!

(+) Some plugins offer a *"Source"* feature, which contains only the source code of the plug-in. These are not essential, you need them only if you would like to help us debug the code. Otherwise, you can omit them. 

(++) After the installation, Eclipse asks if it should be restarted. You can safely install all three plug-ins before restarting it. Also, Eclipse 3.7.2 tend to crash during the restart after installing a new plugin under Win x64, don't be frightened :-) Just start it again by double-clicking on its icon, everything will be fine.

## Using the plugin ##

Switch to the Scala perspective, and create a simple Scala project. Add all the libraries under the `lib` directory to the project as an external JAR. Do this by right-clicking on the project, select *Build Path --> Add External Archives...* (select multiple ones by using the shift or control keys).

After all the dependencies are added to the project, you can use the plugin!

*(This step is required because some of the work hasn't been pushed to any public Maven repositories, so they are unavailable for Sbt/Maven/Ivy projects.)*

### About the Dependencies... ###

Basically the dependencies you have to add to your project are the ScalaTest and Specs2 libraries (with their transitive dependencies).
However, there are three additional libraries there: the i) `scalatest-finders`, ii) `spec-runner` and iii) `specs2-runner` Jar files.

Unfortunately, these libraries are not available from any public repos at the moment. The binary of i) and ii) must be built directly from the ScalaTest project SVN repository. See [this thread for i)][testFinders] and [this pull request for ii)][specRunner].

You can [find the project for iii) here][specs2Runner] which you can build with Sbt. If you would like to build it on your own, you have to put i) and ii) into your local repository (detailed description can be found at the linked project page).

## Issue reporting ##

In case you have any problems, feature requests, anything, I would be more than glad to hear them!

Please file an issue here:

https://github.com/rlegendi/specs2-runner/issues

An important help for the investigation would be your current configuration and the content of the log files. You can find them under *Help --> About Eclipse --> Installation Details --> Configuration* (there is also a button for *View Error Log*).

## Acknowledgement ##

I've got great feedbacks, thanks for the help and work, guys!

* [Guillaume Massé](https://github.com/MasseGuillaume) for testing the plugin under MacOS X with JDK 6.0

## Notes ##
The scalatest plugin was built by:

	$ mvn clean install -P scala-ide-master-scala-2.9

  [projectSite]:    http://rlegendi.github.com/specs2-runner/
  [eclipseIni]:     http://wiki.eclipse.org/Eclipse.ini#Specifying_the_JVM
  [IndigoDownload]: http://www.eclipse.org/downloads/packages/release/indigo/sr2
  [testFinders]:    https://groups.google.com/d/msg/scala-ide-dev/A-jWSJaotfQ/R4IpykP8ldYJ
  [specRunner]:     https://github.com/scala-ide/scala-ide/pull/94
  [specs2Runner]:   https://github.com/rlegendi/specs2-runner

