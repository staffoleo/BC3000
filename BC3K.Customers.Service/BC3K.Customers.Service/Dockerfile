FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as build-env
WORKDIR /app

COPY BC3K.Customers.Service/BC3K.Customers.Service.csproj src/Customers.Service/
RUN dotnet restore "src/Customers.Service/BC3K.Customers.Service.csproj"

COPY ./BC3K.Customers.Service ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "BC3K.Customers.Service.dll"]
