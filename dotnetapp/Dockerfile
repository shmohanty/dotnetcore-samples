FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /source

# TODO: Copy source code to workdir 
COPY *.csproj ./

# TODO: Restore Dot Net Layers
RUN dotnet restore


WORKDIR /source/dotnetapp
COPY *.csproj ./

# TODO: publish app and libraries to /app path
RUN dotnet publish -c Release -o out


WORKDIR /app

# Launch .NET app by providing the command
#CMD
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "dotnetapp.dll"]
