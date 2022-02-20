<script>
  import { Router, Route, Link } from "svelte-navigator";
  import Login from "./Login.svelte";
  import PrivateRoute from "./PrivateRoute.svelte";
  import { user } from "./stores";

  function handleLogout() {
    $user = null;
  }

</script>

<Router>
  

    <nav class=" flex justify-content-end">
      <Link to="/">Home</Link>
      <Link to="about">About</Link>
      <Link to="profile">Profile</Link>
    </nav>


    <header>
    <h1 class="text-5xl font-bold text-center">History</h1>
  </header>

  <main class="text-center">
    <Route path="login">
      <Login />
    </Route>

    <Route path="/">
      <h3 class="text-3xl font-bold ">Home</h3>
      <p>Home sweetl home...</p>
    </Route>

    <Route path="about">
      <h3>About</h3>
      <p>That's what it's all about!</p>
    </Route>

    <PrivateRoute path="profile" let:location>
      <h3>Welcome {$user.username}</h3>
      <button on:click={handleLogout}>Logout</button>
    </PrivateRoute>
  </main>
</Router>
