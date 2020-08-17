# MyOrchardCoreCMS
An Example of Creating a Orchard Core Content Management System Application using NuGet packages with Visual Studio


## YouTube Video
[![OrchardSkillsYouTubeThumbNailCICD](https://www.youtube-nocookie.com/embed/7F00sYlhtno)]https://youtu.be/3pPyNKJo1iU)


## PDF Version of the Documentation
[Getting-Started-with-Orchard-Core.pdf](https://github.com/orchardcmsnet/MyOrchardCoreCMS/files/4000778/Getting-Started-with-Orchard-Core.pdf)

# Introduction

In this article, you're going to see how easy it is to get Orchard Core running in your very own ASP.NET Core Web Application using Visual Studio. You’ll be using the power of the Orchard Core NuGet packages to simplify the process.

## Create a new ASP.NET Core Web Application

First, launch Visual Studio, and create a new ASP.NET Core Web Application:

![Getting-Started-with-Orchard-Core-001](https://user-images.githubusercontent.com/58791170/71449873-6f65e780-2714-11ea-83b1-73087907f6da.png)

Select the box button at the lower left of the screen, “Create a new project”.

![Getting-Started-with-Orchard-Core-002](https://user-images.githubusercontent.com/58791170/71449874-6f65e780-2714-11ea-8108-6f17fe848de3.png)

Select the ASP.NET Core Web Application that is highlighted in blue and press the “Next” button.

![Getting-Started-with-Orchard-Core-003](https://user-images.githubusercontent.com/58791170/71449875-6f65e780-2714-11ea-977d-f3ce83579682.png)

Enter a project name, location, and a solution name. It’s customary to add a “.Web” to specify the project is a web application. The Solution can be whatever you decide. Anther customary practice is to put all the source code in a root “src” folder. Again, it’s up to you to decide how you want to structure your code.

![Getting-Started-with-Orchard-Core-004](https://user-images.githubusercontent.com/58791170/71449876-6f65e780-2714-11ea-8316-7cef1fbcfb39.png)

At the time of writing this article, Orchard Core is based on ASP.NET Core version 3.0. Make sure you select “ASP.NET Core 3.0” in the top right combo. Select the “Empty” template and then press the “Create” button.

## Create“NuGet.config”

In order to utilized the latest code, use the  dev packages, by adding the Orchard Core Preview Feed. Create the fie “NuGet.config” in the root folder and add the following configuration.

![Getting-Started-with-Orchard-Core-005](https://user-images.githubusercontent.com/58791170/71449877-6f65e780-2714-11ea-81ec-56e6186fe4ad.png)

Nuget.config:

```
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <packageSources>
        <add key="Orchard Core Preview Feed" value="https://www.myget.org/F/orchardcore-preview/api/v3/index.json" />
    </packageSources>
</configuration>
```
## Modify Startup Code and Add the Orchard Core Preview Feed to your NuGet Package Manager Package Sources

![Getting-Started-with-Orchard-Core-006](https://user-images.githubusercontent.com/58791170/71449878-6ffe7e00-2714-11ea-9831-6a724af87bef.png)

Update code block to add Orchard Core CMS.

```
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

namespace MyOrchardCoreCMS.Web
{
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
            services.AddOrchardCms();
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }

            app.UseOrchardCore();
        }
    }
}

```

![Getting-Started-with-Orchard-Core-007](https://user-images.githubusercontent.com/58791170/71449879-6ffe7e00-2714-11ea-8648-c4f97696a72c.png)

Right Click on "Dependemncies" and select "Manage NuGets Packages".

![Getting-Started-with-Orchard-Core-008](https://user-images.githubusercontent.com/58791170/71449880-6ffe7e00-2714-11ea-8637-aa14800fd733.png)

Click on the gear icon in the Nuget Package Manager.

![Getting-Started-with-Orchard-Core-010](https://user-images.githubusercontent.com/58791170/71449882-70971480-2714-11ea-87fe-8c2eaf8127f6.png)

Verify the Orchard Core Preview Feed package source is the first entry and that the URL is correct.
Name: Orchard Core Preview Feed
Source: https://www.myget.org/F/orchardcore-preview/api/v3/index.json
Press "OK" to continue.

![Getting-Started-with-Orchard-Core-009](https://user-images.githubusercontent.com/58791170/71449881-70971480-2714-11ea-95be-5c2f2c184946.png)

## Install OrchardCore.Application.CMS.Targets

Select the “Browse” tab in the NuGet Package Manager Window. Enter “OrchardCore.Application.CMS.Targets” in the Search edit box. Make sure the check box “Include prereleases is checked.

Select the package “OrchardCore.Application.CMS.Targets”

![Getting-Started-with-Orchard-Core-011](https://user-images.githubusercontent.com/58791170/71449883-70971480-2714-11ea-9843-ec805a760478.png)

Press the “install” button.

Wait until all the packages are installed.

![Getting-Started-with-Orchard-Core-012](https://user-images.githubusercontent.com/58791170/71449884-712fab00-2714-11ea-91b5-db4669a03da1.png)

Allow Visual Studio to make changes by selecting the “OK” button.

![Getting-Started-with-Orchard-Core-013](https://user-images.githubusercontent.com/58791170/71449885-712fab00-2714-11ea-8342-d5e812b94791.png)

Select the “I Accept” button to accept the license agreement.

![Getting-Started-with-Orchard-Core-014](https://user-images.githubusercontent.com/58791170/71449886-712fab00-2714-11ea-94b8-14cbeef22390.png)

## Run the Application

Select “MyOrchardCoreCMS.Web” and click on the green play button to run the application.

![Getting-Started-with-Orchard-Core-015](https://user-images.githubusercontent.com/58791170/71449887-712fab00-2714-11ea-9940-0aac74b86f7d.png)

Select “Yes” button to trust the self-signed certificate.

![Getting-Started-with-Orchard-Core-016](https://user-images.githubusercontent.com/58791170/71449888-712fab00-2714-11ea-84ec-19278c37eae3.png)

Select “Yes” button to install certificate.

![Getting-Started-with-Orchard-Core-017](https://user-images.githubusercontent.com/58791170/71449889-71c84180-2714-11ea-9dfd-cb8d51e8c7fc.png)

A logging window will appear displaying debug information.

![Getting-Started-with-Orchard-Core-018](https://user-images.githubusercontent.com/58791170/71449890-71c84180-2714-11ea-9ac7-d1d59c779ae9.png)

Congratulations! Your Orchard Core Web Application will now be running in the default web browser.

A Setup page will be displayed. Enter the “name of your site”, “Blog” for Recipe, your “default time zone”, “Sqlite” for the database, a “user name” and password. Press the “Finish Setup” button to complete the process.

![Getting-Started-with-Orchard-Core-019](https://user-images.githubusercontent.com/58791170/71449891-71c84180-2714-11ea-962c-fa8bb36ec610.png)

Navigate to the admin dashboard page by specifying “/admin” at the end of the URL. i.e. https://localhost:5001/admin. Login with your credentials.

![Getting-Started-with-Orchard-Core-020](https://user-images.githubusercontent.com/58791170/71449893-7260d800-2714-11ea-95ec-d8fb97e1e112.png)

Enter in your credentials and press the "Log in" button.

![Getting-Started-with-Orchard-Core-021](https://user-images.githubusercontent.com/58791170/71449894-7260d800-2714-11ea-8384-b706570ba8dc.png)

You are now ready to configure and create content for your Orchard Core Web Application.

## Conclusion

With just a new few lines of code and some configuration, it is easy to create a Content Management System with ASP.NET Core and Orchard Core CMS.

## GitHub

The complete source code is located [here](https://github.com/orchardcmsnet/MyOrchardCoreCMS).
