SimpleCamel
===========

This example just contains a blueprint file with a camel context and a route.

Run in Karaf-4.0.3
------------------

karaf@root()> feature:repo-add camel 2.15.5
...OR...
karaf@root()> feature:repo-add mvn:org.apache.camel.karaf/apache-camel/2.15.5/xml/features

karaf@root()> feature:install camel-blueprint camel-stream

Check if feature was installed
karaf@root()> feature:list | grep camel-blueprint


Copy the file simple-camel-blueprint.xml into the deploy folder of karaf

karaf@root()> list | grep simple-camel

Should show something like that:
[ 168] [Active     ] [Created     ] [       ] [   60] simplecamel.xml (0.0.0)
...OR...
78 | Active |  80 | 0.0.0   | simple-camel-blueprint.xml


karaf@root()> la | grep simple-camel-blueprint

You will see "Hello World" printed to the karaf console every 5 seconds.

Test
----

As karaf listens to changes to the files in the deploy folder you can change the file and save to update it in karaf.
Open the file simple-camel-blueprint.xml in the deploy folder using a text editor.

Change "stream:out" to "log:simplecamel" and save the file.

Now the the console should not show any more Hello World and instead the lines should go to the karaf log.

> log:display

Should show lines like:
2011-12-29 16:26:48,104 | INFO | simple | simplecamel | ache.camel.processor.CamelLogger   87 | 84 - org.apache.camel.camel-core - 2.8.2 | Exchange[ExchangePattern:InOnly, BodyType:String, Body:Hello World]

