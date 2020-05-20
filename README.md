# Android-Studio-Project-With-API26
step by step to setting for using API 26(Android lib)

### step 1 :
gradle-wrapper.properties

    distributionUrl=https\://services.gradle.org/distributions/gradle-5.4.1-all.zip
    // change to 
    distributionUrl=https\://services.gradle.org/distributions/gradle-3.3-all.zip
    
### step 2 :
build.gradle(app)

    dependencies {
        implementation fileTree(dir: 'libs', include: ['*.jar'])
        implementation 'androidx.appcompat:appcompat:1.1.0'
        implementation 'androidx.constraintlayout:constraintlayout:1.1.3'
        testImplementation 'junit:junit:4.12'
        androidTestImplementation 'androidx.test.ext:junit:1.1.1'
        androidTestImplementation 'androidx.test.espresso:espresso-core:3.2.0'
    }
    // change to 
    dependencies {
        compile fileTree(include: ['*.jar'], dir: 'libs')
        compile "com.android.support:appcompat-v7:26.1.0"// for support appcompatActivity
        
        compile 'com.android.support.constraint:constraint-layout:1.0.2'// for support constraintLayout 
    }
    
    
    compileSdkVersion 29
    buildToolsVersion "29.0.2"
      targetSdkVersion 29
    // change to
    compileSdkVersion 26
    buildToolsVersion "26.0.0"
      targetSdkVersion 26
    
    
### step 3 :
build.gradle(Project)

    buildscript {
        repositories {
            google()
            jcenter()
        }
        dependencies {
            classpath 'com.android.tools.build:gradle:3.5.1'

            // NOTE: Do not place your application dependencies here; they belong
            // in the individual module build.gradle files
        }
    }

    allprojects {
        repositories {
            google()
            jcenter()
        }
    }
    // change to 
    buildscript {
        repositories {
            jcenter()
            mavenCentral()
            maven {
                url 'https://maven.google.com/'
                name 'Google'
            }
        }
        dependencies {
            classpath 'com.android.tools.build:gradle:2.3.1'

            // NOTE: Do not place your application dependencies here; they belong
            // in the individual module build.gradle files
        }
    }

    allprojects {
        repositories {
            jcenter()
            maven {
                url 'https://maven.google.com/'
                name 'Google'
            }
        }
    }
    
### step 4 :
MainActivity.java

    import androidx.appcompat.app.AppCompatActivity;
    // replace to 
    import android.support.v7.app.AppCompatActivity;


main.xml (刪除 再加(否則會找錯資源導致crash)):
 
    <androidx.constraintlayout.widget.ConstraintLayout
    // delete androidx.constraintlayout.widget.ConstraintLayout
    // and then keyin to add android.constraintlayout.widget.ConstraintLayout
    <android.constraintlayout.widget.ConstraintLayout
