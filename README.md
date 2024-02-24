### Project Setup

1. Create new project `ASP.NET Core Web Application` with MVC template and named `MvcEfCore` (use `Individual User Accounts` for Authentication)

### Model Classes

1. Create new class `Models/Team` with props
   - TeamName: `string` annotated with `[Key]` and `[MaxLength(30)]`
   - City: `string`
   - Province: `string`
   - Country: `string`
   - Players: `List<Player>`
2. Create new class `Models/Player` with props
   - PlayerId: `int` (`<className>Id` or `Id` will be the default key)
   - FirstName: `string`
   - LastName: `string`
   - Position: `string`
   - TeamName: `string` (foreign key maps to primary key of the `Team` class)
   - Team: `Team`

### Database Context

1. In `Data/ApplicationDbContext.cs`, add prop
   - Teams: `DbSet<Team>`
   - Players: `DbSet<Player>`
2. In `appsettings.json`, change the database name to `NHL` in the `ConnectionStrings`

### Dummy Data

1. Copy and paste the downloaded `DummyData.cs` into `Data` folder
2. In `Startup.cs`, add `DummyData.Initialize(app)` to run the `DummyData.cs` when the app is started

### Migration

1. In PM Console, run
   (using .NET utility)

   - `dotnet ef migrations add "nhl"` >> generate the fluid API for teams & players
   - `dotnet ef database update` >> create tables in the DB

   (using NuGet package)

   - `add-migration "nhl"`
   - `update-database`

### Controllers

1. Create new controller `Add MVC Controller with views, using Entity Framework` for both teams and players
2. In `_Layout.cshtml`, add two `li` in the NavBar for `Teams` and `Players`
