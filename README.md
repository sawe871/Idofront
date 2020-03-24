![CI](https://github.com/MineInAbyss/Idofront/workflows/Java%20CI/badge.svg)
# Idofront

Idofront is a repository, shadowed by many of our plugins, which contains many useful helper functions. Some are exclusive in usefulness to code written in Kotlin.

This project is really new and not intended to be used by anyone for their own plugins yet! Don't expect any consistency or good code for now.

### Features

- Many helper functions to reduce boilerplate code, such as:
    - `String.color()` to translate color codes.
    - Quick ItemStack manipulation:
        ```kotlin
        itemStack.editItemMeta{
            isUnbreakable = true
            setDisplayName("Custom name")
        }
        ```
- A clean command DSL for kotlin (May change a lot in the near future). See implementation in our plugins, notably [Mobzy](https://github.com/MineInAbyss/Mobzy/blob/master/src/main/java/com/mineinabyss/mobzy/MobzyCommands.kt).

##### Coming soon(tm):

- Yaml/Json serialization of common Bukkit classes with kotlinx.serialization and kaml. Use the wrappers in your constructor and convert to and from spigot items with ease!
- Easy custom recipe registration.


### Setup

- Depend on [KotlinSpice](https://github.com/CultOfClang/KotlinSpice) in your plugin config, and request users to download
the plugin to their server.
- Or: Manage [shading](https://imperceptiblethoughts.com/shadow/) Kotlin, kotlinx.serialization, and other Kotlin libraries we use depending on what you are using in your project. Shading Kotlin can cause hard-to-find errors if two different versions are present during runtime! 

#### Gradle:

Add the following repository to your build.gradle:

```groovy
repositories {
    maven {
        name = "Idofront"
        url = uri("https://maven.pkg.github.com/MineInAbyss/Idofront")
        credentials {
            username = project.findProperty("gpr.user") ?: System.getenv("GITHUB_ACTOR")
            password = project.findProperty("gpr.key") ?: System.getenv("GITHUB_TOKEN")
        }
    }
}
```

Set your username and Github token your global gradle properties`~/.gradle/gradle.properties`. Learn more about this [here](https://help.github.com/en/packages/using-github-packages-with-your-projects-ecosystem/configuring-gradle-for-use-with-github-packages#authenticating-to-github-packages). (Hopefully Github stops forcing you to do this soon!)

Add the following dependency:

```groovy
dependencies {
    implementation 'com.mineinabyss:idofront:<version>'
}
```

You can find the available versions in the packages tab of this project on Github.